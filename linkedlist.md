## LinkedList Java

### Initialized Node

```java
 1 --> 2 ---> 3---> 4--->5
 class Node {
        int val;
        Node next;
        public Node(int val) {
            this.val = val;
        }
    }
```

### Get Specific Index Value

```java
  public int get(int index) {
         if (index >= size) return -1; // check ensure the size > index
        Node current = head;  // replicate the Node 
        for (int i = 0; i < index; i++) {
            current = current.next; // Loop until the specific index 
        }
        return current.val; // return the val
    }
```

### Add the val infront of the current Node

```java
public void addAtHead(int val) {
        Node prev = head; // create new Node to initialize the current node
        head = new Node(val); // current node to equal the new val node
        head.next = prev;    // set the next node of the new node to prev
        size ++;            // increase the size of node
    }
```

### Add the val tail of the current Node

```java
 public void addAtTail(int val) {
        Node temp = new Node(val);  // initialize new node
        size ++; // increase the size
        if(head == null){  // current node is empty straigthway add
            head = temp;
        }else{
            Node current = head;  // replicate the current node
            while(current.next != null){ // loop until the current.next is null
                current = current.next;
            }
            current.next = temp; // point the current.next to the new node
        }

    }
```

### Add the val to specific index

```java
    public void addAtIndex(int index, int val) {
        if(index > size){ // index not valid
            return 
        }
        if(index == 0){ // current node is empty so add
            addAtHead(val);
        }else{
            size ++;   // increase the size 
            Node temp = new Node(val); // create new node for the new val
            Node current = head; // replicate the current node
            for(int i = 0; i<index; i++){
                current = current.next;  // loop until to specific index
            }

            temp.next  =  current.next; // point the new node of next to current.next
             current.next = temp; // current.next  point back to new node
        }
    }
```

### Linked-List Cycle

Given the `head` of a linked list, return *the node where the cycle begins. If there is no cycle, return* `null`.

![](https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png)

Define two pointers slow and fast. <mark>Both start at head node, fast is twice as fast as slow</mark>. <mark>If it reaches the end it means there is no cycle</mark>, otherwise eventually it will eventually catch up to slow pointer somewhere in the cycle.

Let the distance from the first node to the the node where cycle begins be A, and let say the slow pointer travels travels A+B. The fast pointer must travel 2A+2B to catch up. The cycle size is N. Full cycle is also how much more fast pointer has traveled than slow pointer at meeting point.

From our calculation slow pointer traveled exactly full cycle when it meets fast pointer, and since originally it travled A before starting on a cycle, it must travel A to reach the point where cycle begins! We can start another slow pointer at head node, and move both pointers until they meet at the beginning of a cycle.

```java
public class Solution {
            public ListNode detectCycle(ListNode head) {
                ListNode slow = head;
                ListNode fast = head;

                while (fast!=null && fast.next!=null){
                    fast = fast.next.next;
                    slow = slow.next;

                    if (fast == slow){
                        ListNode slow2 = head; 
                        while (slow2 != slow){
                            slow = slow.next;
                            slow2 = slow2.next;
                        }
                        return slow;
                    }
                }
                return null;
            }
        }
```

### 
