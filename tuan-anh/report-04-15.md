JSX 
- JSX (JavaScript XML) là một extension của JavaScript
cho phép chúng ta viết HTML trong React một cách dễ dàng 
hơn bình thường

- With JSX:
    <div className='menu' />
- In JavaScript:
    React.createElement(
        'div',
        {className: 'menu'}
    )

- Có thể viết expression trong JSX như sau:
    <h1>Jake has {1 + 2} apples</h1>