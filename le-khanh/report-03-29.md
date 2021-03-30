# This trong callback và closure:

## Với this trong call back, this sẽ không được trỏ tới this trong đối tượng sở hữu phương thức đó, mà được gán bằng đối tượng mà nó được gọi

- ví dụ:

  ```javascript
  let person = {
    name: "khanh",
    age: 25,
    spell: function () {
      console.log(this.name + " " + this.age);
    },
  };
  setTimeout(person.spell, 5000); // undefined
  ```

- Trong ví dụ trên sẽ trả về undefined vì this đã được tham chiếu tới object toàn cục là window.
- Cách giải quyết: Bind phương thức spell cho đối tượng person.

  ```javascript
  setTimeout(person.spell.bind(person), 5000); //log ra khanh 25
  ```

## Với this trong closure:

- this không tham chiếu tới this của hàm bên ngoài vì nó chỉ tham chiếu tới this của chính hàm mà nó được sử dụng mà thôi.
- Khi không có tham chiếu cụ thể, this sẽ được gán cho object toàn cục và undefined trong strict mode.
- Ta có thể gán this cho một biến ở hàm bên ngoài, như vậy trong closure có thể truy cập tới giá trị của this.
- Ví dụ:

  ```javascript
  let group = {
    admin: "Phanh",
    Member: ["Khanh", "Manh", "TAnh", "Hieu", "Loc"],
    spell: function () {
      this.Member.forEach(function (mem) {
        console.log(mem + " manage by " + this.admin); // this.admin = undefined
      });
    },
  };
  group.spell();
  ```

  - Trong ví dụ trên this.admin sẽ là undefined.
  - Để khắc phục điều này, ta gán this thành that ở hàm ngoài, khi đó có thể sử dụng object group mà this tham chiếu tới.

  ```javascript
  let group = {
    admin: "Phanh",
    Member: ["Khanh", "Manh", "TAnh", "Hieu", "Loc"],
    spell: function () {
      let that = this; // gán this cho that
      this.Member.forEach(function (mem) {
        console.log(mem + " manage by " + that.admin);
      });
    },
  };
  group.spell();
  ```
