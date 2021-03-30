
Spread and Rest Operator:
-Là syntax mới của ES6, giúp chúng ta có thể thao tác với function argument, phần tử của 
array và object dễ dàng hơn
-Spread có thể "spread" các phần tử trong array theo cách dễ dàng
    const arr = [1, 2, 3]
    const newArr = [...arr] 
    // newArr = [1, 2, 3] //newArr là 1 deep copy của arr

-Hay spread phần tử trong 1 object:
    user = {id: 1, firstname: 'Mike'}
    const newUser = {...user}
    // newUser = {id: 1, firstname: 'Mike'} // đây cũng là deep copy của user
