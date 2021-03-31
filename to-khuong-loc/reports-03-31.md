# Làm sao để tạo hiệu ứng fade, slide trong React?

## Ý tưởng :

- toggle class bằng state
- fade: toggle class opacity-0 và opacity-1
- slide: toggle transform, height. Vd: slideDown-Up thì toggle translateY(-100%) + height 0; và translateY(0)+ height 100%

## Thực hiện

### Slide Up - Down animation on Navbar - sm screen

```javascript
import React, { useState } from "react";
import { Link } from "react-router-dom";

// Tạo component Navbar;
// css: tailwindcss
const Navbar = () => {
  // Tạo state để toggle class
  const [isShow, setIsShow] = useState(false);

  return (
    <nav className="px-1 py-2 bg-gray-900 flex flex-col md:flex-row text-white sticky z-30">
      <div className="flex items-center">
        <Link className="ml-2" to="/">
          VMO training
        </Link>
        <span className="ml-auto mr-2 md:hidden">
          <i onClick={() => setIsShow(true)} className="fas fa-bars"></i>
        </span>
      </div>
      // toggle class dựa trên isShow // nếu isShow === false -> menu bị dịch chuyển
      lên trên 100%, chiều cao thu dần về 0; // nếu isShow === true -> menu dịch
      về vị trí cũ, chiều dài tăng dần lên 100% // note: phải có transition + duration
      <div
        className={`p-4 bg-gray-900 flex flex-col md:justify-center md:flex-1 md:flex-row transition duration-700 overflow-hidden absolute w-full left-0 top-0 transform md:relative ${
          isShow
            ? "translate-y-0 md:translate-y-0"
            : "-translate-y-full md:translate-y-0"
        }`}
      >
        <div className="text-right absolute right-0">
          <i
            onClick={() => setIsShow(false)}
            className="fas fa-times md:hidden mr-4"
          ></i>
        </div>
        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/"
        >
          Home
        </Link>
        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/counter"
        >
          Counter
        </Link>

        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/quotes"
        >
          Quotes
        </Link>
        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/todos"
        >
          Todos
        </Link>
        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/caculator"
        >
          Caculator
        </Link>

        <Link
          onClick={() => setIsShow(false)}
          className="md:ml-2 md:mx-5 md:text-lg"
          to="/test"
        >
          Test
        </Link>
      </div>
    </nav>
  );
};

export default Navbar;
```

## Lưu ý

Nếu component bị unmount trước khi hiệu ứng kết thúc thì setTimeout một khoảng thời gian tương đương hoặc nhiều hơn thời gian hiệu ứng

```javascript
// slide mất 700ms thì delay 700 trước khi rerender

const onHandleClick = () => {
  setTimeout(() => {
    // do somthing rerender
  }, 700);
};
```
