# Queue's


A queue is a data structure that follows the FIFO (First In First Out) principle. This means that the first element added to the queue will be the first one to be removed.

my_queue = ["last", "middle", "first"]

#### Enqueue
Adding an element to the queue is called enqueue. This is done at the rear of the queue.

#### Dequeue
Removing an element from the queue is called dequeue. This is done at the front of the queue.

#### Peek
Peek is used to get the element at the front of the queue without removing it.

#### Implementation
```python
class Queue:
    def __init__(self):
        self.queue = []
    
    def enqueue(self, data):  # Add element to the rear of the queue
        self.queue.append(data)
    
    def dequeue(self):  # Remove element from the front of the queue
        if len(self.queue) < 1:
            return None
        return self.queue.pop(0)
    
    def peek(self):   # Get the element at the front of the queue
        if len(self.queue) < 1:
            return None
        return self.queue[0]
    
    def display(self):  # Display the queue
        print(self.queue)
```
