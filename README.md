class Stack(object):
	def __init__(self):
		self.stack = []

	def pop(self):
		if self.is_empty():
			return None
		else:
			return self.stack.pop()

	def push(self,val):
		return self.stack.append(val)

	def size(self):
		return len(self.stack)

	def is_empty(self):
		return self.size() == 0

	def peak(self):
		if self.is_empty():
			return None
		else:
			return self.stack[-1]


class Queue(object):
	def __init__(self):
		self.queue = []

	def enqueue(self,val):
		self.queue.insert(0,val)

	def dequeue(self):
		if self.is_empty():
			return None
		else:
			return self.queue.pop()

	def is_empty(self):
		return self.size() == 0
	def size(self):
		return len(self.queue)
#
# s = Stack()
# s.push(1)
# s.push(2)
# s.push(3)
# d = s.peak()
# print(s.stack)
# print(d)


#实现一个栈来模拟一个队列
class QueueByStack(object):
	def __init__(self):
		self.queue1 = Stack()
		self.queue2 = Stack()

	def enqueue(self,val):
		self.queue1.push(val)

	def dequeue(self):
		for i in range(self.queue1.size() - 1):
			value = self.queue1.pop()
			self.queue2.push(value)

		res = self.queue1.pop()
		for i in range(self.queue2.size()):
			value = self.queue2.pop()
			self.queue1.push(value)

		return res

	def is_empty(self):
		return self.queue1.is_empty()

	def size(self):
		return self.queue1.size()

def insertSort(A):
    for j in range(1, len(A)):
        key = A[j]
        i = j - 1
        while i >= 0 and A[i] > key:
            A[i + 1] = A[i]
            i = i - 1
        A[i + 1] = key
    return A

A = [5, 2, 4, 6, 1, 3]

print(insertSort(A))
