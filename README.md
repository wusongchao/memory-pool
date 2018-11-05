# memory-pool

This is a by-product when i am doing my compile lesson's work. In the phase of RE to NFA, i have to create a lot of state and edge on the heap. So thanks for 大牛vzch's advice, i try to implement a pool to manage the construction and destruction.

So, this is not an actual "memory-pool", for each instantiated template FixedMemoryPool, it can only create one kind of object, and you can't deallocate during the Pool's lifecycle. All objects's destruction is finished at the pool's destruction phase.

```cpp
FixedMemoryPool<A> pool;
A* a1 = pool.newElement(1, 2);
```

It's not strict with only the RE to NFA conversion. Since in RE to NFA conversion, i don't need to append destructor for ```State``` or ```Edge```, i just need to maintain two pools.

But this "pool" will call its objects destructor (more general).

I am still confused about the operator new/delete..., so it's a great pleasure for me to accept other's advice, for example, is this implementation safe? Also, i am really looking forward to receive more test cases to test this naive implementation (though i know no one will look at this repo, and i am just typing for myself).

Also, for the code, i am eager to receive some advices.
