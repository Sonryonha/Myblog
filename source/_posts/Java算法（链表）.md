---
title: Java算法练习（链表）
categories: 
- Java
tags: 
- Java算法
- 链表
---
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode removeElements(ListNode head, int val) {
        // 判断头结点是否为空，为空直接返回头结点对应的链表
        if (head == null) {
            return head;
        }
        // 设置虚拟节点，在head的前面，作为虚拟head
        ListNode dummy = new ListNode(-1, head);
        // 为虚拟节点的索引值创建变量
        ListNode pre = dummy;
        // 为头节点的索引值创建变量
        ListNode cur = head;
        while (cur != null) {
            // 当头结点对应的值不为目标值时，把虚拟节点向后移动一位
            if (cur.val != val) {
                pre = cur;
            }else {
                // 当头结点对应的值为目标值时，使虚拟节点直接指向头结点的下一位节点实现删除节点
                // java中不用手动清除非目标节点的值，GC会自动清理
                pre.next = cur.next;
            }
            // 最后头结点再向后移动一位继续进行循环判断
            cur = cur.next;
        }
        // 返回删除后的链表
        return dummy.next;
    }
}

```