# Inheritance in ES6

- Trong ES5: ta sẽ tạo contructor sau đó inheritance và inheritance chain theo prototype

  ```javascript
  function Animal(legs) {
    this.legs = legs;
  }

  Animal.prototype.walk = function () {
    console.log("walking on " + this.legs + " legs");
  };

  function Bird(legs) {
    Animal.call(this, legs);
  }

  Bird.prototype = Object.create(Animal.prototype);
  Bird.prototype.constructor = Animal;

  Bird.prototype.fly = function () {
    console.log("flying");
  };

  var pigeon = new Bird(2);
  pigeon.walk(); // walking on 2 legs
  pigeon.fly(); // flying
  ```

- Với ES6: ta dùng class, bản chất của class là function nhưng khác với `constructor function`,

  - Cú pháp của `class` hướng theo các ngôn ngữ OOP hơn. Khi khởi tạo một object, `class` auto run `constructor method`. Với `constructor function`.
  - Để thêm một method ta thêm qua `constructorName.prototype.methodName = f`, nhưng với `class`, ta viết method trong `class`.
  - Các method của `constructor function` đều là `enumerable`, để chuyển thành `non-enumerable` ta phải dùng `Object.defineProperty()` function .Còn với class các method là `non-enumerable`
  - Vì class là một function đặc biệt nên nó có thể truyền class vào một function như arg, gán class cho một biến, trả về trong một function.
  - Để inheritence trong class, ta dùng keyword `extend`

  ```javascript
  class Animal {
    constructor(legs) {
      this.legs = legs;
    }
    walk() {
      console.log("walking on " + this.legs + " legs");
    }
  }

  class Bird extends Animal {
    constructor(legs) {
      super(legs);
    }
    fly() {
      console.log("flying");
    }
  }

  let bird = new Bird(2);

  bird.walk();
  bird.fly();
  ```

  - Trong class con, nếu có method trùng tên với method cha sẽ ghi đè method của method cha.
  - Có thể extend từ các kiểu built-in như `map`, `array`, `set`

  ```javascript
  class Queue extends Array {
    enqueue(e) {
      super.push(e);
    }
    dequeue() {
      return super.shift();
    }
    peek() {
      return !this.empty() ? this[0] : undefined;
    }
    empty() {
      return this.length === 0;
    }
  }

  var customers = new Queue();
  customers.enqueue("A");
  customers.enqueue("B");
  customers.enqueue("C");

  while (!customers.empty()) {
    console.log(customers.dequeue());
  }
  ```
