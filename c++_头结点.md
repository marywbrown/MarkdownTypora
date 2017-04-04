#### 头结点

​        链表中的每一个点叫做结点，指向结点的叫做指针。

​	头结点就是在链表的初始定义一个没有值的结点，并使结点中的地址指向下一个地址。

```c++
struct node
{
  int val;
  struct node *next; 
}
```

```c++
struct node head;   // 因为head是结点，所以没有* ，struct 这里可省略 ，下面也是
struct node first;  // first这里指的是链表本身的1个结点
head.next = &first;
```

#### 头指针



​        头指针则是指指向头节点的地点的指针，无论链表是否为空，头指针均不为空。头指针是链表的必要元素。我们在上面的代码中加入下面代码来定义头指针。

```c++
struct node *point = &head
```

#### 例子

​	这是leetcode上面一道关于合并两个有序链表的题目：Merge Two Sorted Lists

​	我们发现当在结构体中已经初始化结点的时候，头结点需要附一个int值，我们通常令他为-1，其实其他值也没有影响，这是一个常规做法。

```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */

class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) 
    { 
    	ListNode head(-1);
    	ListNode *cur = &head;
    	while(l1 && l2)
    	{
    		if(l1->val > l2->val)
    		{
    		cur->next = l2;
    		l2 = l2->next;
    	    } 
    	    else
    	    {
    		cur->next = l1;
    		l1 = l1->next;
    	    }
    	    cur = cur->next;
    	}
    	if(l1==NULL)
    	{
    	   cur->next = l2;
    	}
    	else
    	{
    	    cur->next = l1;
    	}
    	return head.next;
    }
    
};
    
```