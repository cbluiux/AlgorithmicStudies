```javascript
/**
 * Initialize your data structure here.
 */
var MyQueue = function () {
  this.inbox = [];
  this.outbox = [];
};

/**
 * Push element x to the back of queue.
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function (x) {
  this.inbox.push(x);
};

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function () {
  if (this.outbox.length === 0) {
    while (this.inbox.length > 0) {
      this.outbox.push(this.inbox.pop());
    }
  }
  return this.outbox.pop();
};

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function () {
  if (this.inbox.length !== 0) {
    return this.inbox[0];
  }
  if (this.outbox.length !== 0) {
    let pop = this.outbox.pop();
    this.outbox.push(pop);
    return pop;
  }
  return null;
};

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function () {
  return this.inbox.length + this.outbox.length === 0;
};
```
