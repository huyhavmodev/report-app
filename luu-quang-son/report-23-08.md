**Children** -- dùng để thiết kế master layout. giúp các component có thể lồng nội dung vào nhau.
 
 -- Tham khảo : https://viblo.asia/p/tim-hieu-ve-children-trong-react-oOVlYqWol8W 

 **HOC - React.memo** 
        HOC là 1 HÀM CÁI MÀ NHẬN VÀO 1 COMPONENT VÀ TRẢ VỀ 1 COMPONENT MỚI.

```js 
        const EnhancedComponent = higherOrderComponent(WrappedComponent);
```

-- Tham khảo : https://viblo.asia/p/higher-order-components-hoc-trong-react-js-1Je5EvoAKnL


**Redux-Thunk** : 
    -- Redux Thunk là một Middleware cho phép bạn viết các Action trả về một function thay vì một plain javascript object bằng cách trì hoãn việc đưa action đến reducer.
    -- Redux Thunk được sử dụng để xử lý các logic bất đồng bộ phức tạp cần truy cập đến Store hoặc đơn giản là việc lấy dữ liệu như Ajax request.

    -- Luồng của redux : 
    
    ACCTION CREATOR - ACTION - DISPATCH - STORE (MIDDLEWARE) - REDUCERS - STATE.

    -- Tham khảo https://5mtech.vn/tin-tuc/lap-trinh/huong-dan-su-dung-redux-thunk-hooks-ket-hop-cung-react-hooks-api.html