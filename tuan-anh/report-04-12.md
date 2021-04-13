useCallback and useMemo
- useMemo, useCallback nhận vào 1 function và array dependencies 
useMemo trả lại 1 memoized value còn useCallback trả lại 
1 memoized function
// const returnedFunction = useCallback(fn, deps);
// const returendValue = useMemo(fn, deps);

- useMemo sử dụng để tránh việc lặp đi lặp lại những logic
tính toán nặng trong component, tránh re-render không cần thiết
- useCallback ngăn việc tạo mới callback function từ component
cha truyền xuống component con, khiến component con re-render
