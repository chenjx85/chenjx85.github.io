---
layout: post
title: 关于map/unordered_map/set/unordered_set
date: 2019-05-13
categories: blog
tags: [c++知识]
#description: 简单介绍本博客。
---
c++的STL中实现了map和set两种关联容器。

map和set底层都是用红黑树实现的，红黑树是一种非常高效的平衡二叉树，可以实现对数级别时间复杂度的查找与插入。

map和set都会自动对元素排序，所以如果用迭代器输出容器中的元素，输出顺序不一定就是输入到容器中的元素的顺序。

unordered_map和unordered_set，顾名思义，是不排序的map和set，底层用哈希表实现。

unordered_map和unordered_set，用迭代器输出的话，输出顺序应该是哈希表从前往后的顺序，也不可能是输入到容器中的元素的顺序。

测试代码如下。

```c++
#include<iostream>
#include<set>
#include<unordered_set>
using namespace std;
int main()
{
	unordered_set<int>us;
	us.insert(1);
	us.insert(3);
	us.insert(2);
	for(unordered_set<int>::iterator iter=us.begin();iter!=us.end();iter++)
		cout<<*iter<<"  ";
	cout<<endl;
	
	set<int>s;
	s.insert(5);
	s.insert(3);
	s.insert(2);
	s.insert(4);
	s.insert(1);
	for(auto iter=s.begin();iter!=s.end();iter++)
		cout<<*iter<<"  ";
	cout<<endl;
	
	return 0;
}
```

输出是231和12345。

改变一下unordered_set中元素的插入顺序，发现构建的哈希表可能又不一样了，输出也不是固定的231，这个可能是跟哈希冲突方式的设计有关。

改变一下set中元素的插入顺序，发现输出永远都是12345，因此笔者猜测可能set的输出永远都是有序的，中序遍历一下构建的红黑树就输出了。