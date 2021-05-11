# LinkedList Cycle

```javascript
class Node {
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

const hasCycle = (head) => {
  let slow = (fast = head);

  while (fast !== null && fast.next !== null) {
    fast = fast.next.next;
    slow = slow.next;

    if (slow === fast) {
      return true; // found the cycle
    }
  }
  return false; // cycle never found while loop breaks
};

const head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);
head.next.next.next.next.next = new Node(6);
console.log(`Does this LinkedList have a cycle? ${hasCycle(head)}`);

head.next.next.next.next.next.next = head.next.next;
console.log(`Does this LinkedList have a cycle? ${hasCycle(head)}`);

head.next.next.next.next.next.next = head.next.next.next;
console.log(`Does this LinkedList have a cycle? ${hasCycle(head)}`);
```

# Start of LL Cycle

```javascript
class Node {
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

const findCycle = (head) => {
  let cycleLength = 0,
    slow = head,
    fast = head;

  while (fast !== null && fast.next !== null) {
    fast = fast.next.next;
    slow = slow.next;

    if (slow === fast) {
      cycleLength = calcCycleLength(slow);
      break;
    }
  }
  return findStart(head, cycleLength);
};

const calcCycleLength = (slow) => {
  let current = slow,
    cycleLength = 0;

  while (true) {
    current = current.next;
    cycleLength++;

    if (current === slow) {
      break;
    }
  }
  return cycleLength;
};

const findStart = (head, cycleLength) => {
  let slow = head,
    fast = head;

  while (cycleLength > 0) {
    fast = fast.next;
    cycleLength--;
  }

  while (slow !== fast) {
    slow = slow.next;
    fast = fast.next;
  }
  return slow;
};

const head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);
head.next.next.next.next.next = new Node(6);

head.next.next.next.next.next.next = head.next.next;
console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);

head.next.next.next.next.next.next = head.next.next.next;
console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);

head.next.next.next.next.next.next = head;
console.log(`LinkedList cycle start: ${find_cycle_start(head).value}`);
```

# Happy Number

```javascript

```

# Middle of LL

```javascript
class Node {
  constructor(value, next = null) {
    this.value = value;
    this.next = next;
  }
}

const find_middle_of_linked_list = function (head) {
  // TODO: Write your code here
  let fast = head;
  let slow = head;
  // OR statements will always execute both commands
  // AND statements will shortcircuit if the first command cannot resolve to truthy
  while (fast !== null || fast.next !== null) {
    fast = fast.next.next;
    slow = slow.next;
  }
  return slow;
};

head = new Node(1);
head.next = new Node(2);
head.next.next = new Node(3);
head.next.next.next = new Node(4);
head.next.next.next.next = new Node(5);

console.log(`Middle Node: ${find_middle_of_linked_list(head).value}`);

head.next.next.next.next.next = new Node(6);
console.log(`Middle Node: ${find_middle_of_linked_list(head).value}`);

head.next.next.next.next.next.next = new Node(7);
console.log(`Middle Node: ${find_middle_of_linked_list(head).value}`);
```
