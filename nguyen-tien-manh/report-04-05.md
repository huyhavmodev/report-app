# Nguyen Tien Manh - 04/05

## TOPIC: Context

- Context cung cấp phương pháp truyền data xuyên suốt component tree mà không cần phải truyền props một cách thủ công qua từng level.
## Khi nào nên dùng Context 
- Context được thiết kế để chia sẽ data khi chúng được xem là “global data”
- Sử dụng context, chúng ta có thể tránh được việc truyền props qua các elements trung gian
- Nếu chỉ muốn dùng context để tránh việc truyền một số props qua nhiều levels, , component composition thường là một giải pháp đơn giản hơn so với context.
    ```javascript
    <Page user={user} avatarSize={avatarSize} />
    // ... được renders ...
    <PageLayout user={user} avatarSize={avatarSize} />
    // ... được renders ...
    <NavigationBar user={user} avatarSize={avatarSize} />
    // ... được renders ...
    <Link href={user.permalink}>
    <Avatar user={user} size={avatarSize} />
    </Link>
    ```
    - Ví dụ muốn truyền user, avatarSize xuống tận component Link, Avatar. Thay vì dùng Context hoặc truyền liên tục xuống như trên thì so thể dùng cách sau
    ```javascript
    function Page(props) {
    const user = props.user;
    const userLink = (
        <Link href={user.permalink}>
        <Avatar user={user} size={props.avatarSize} />
        </Link>
    );
    return <PageLayout userLink={userLink} />;
    }

    // Now, we have:
    <Page user={user} avatarSize={avatarSize} />
    // ... được renders ...
    <PageLayout userLink={...} />
    // ... được renders ...
    <NavigationBar userLink={...} />
    // ... được renders ...
    {props.userLink}
    ```
    => Chỉ có tầng trên cùng của Page biết Link và Avatar có dùng user, avatarSize
- Tuy nhiên, đôi khi có những data trùng lặp cần được truy cập bởi nhiều components trong component tree, và ở nhiều tầng khác nhau. Context là thích hp
## API
- React.createContext: Tạo một Context object. Khi React render một component mà nó subcribe đến Context object này, nó sẽ đọc giá trị hiện tại của context đó từ Provider gần nhất trên component tree.
    ```javascript
    const MyContext = React.createContext(defaultValue);
    ```
- Context.Provider: Mỗi Context object đi cùng với một Provider React component cho phép consuming component theo dõi sự thay đổi của context đó.
    ```javascript
    <MyContext.Provider value={/* some value */}>
    ```
- Context.Consumer: Tham số value truyền đến function sẽ bằng với value prop của Provider gần nhất trong context này trên tree component. Nếu không có Provider nào cho context này ở trên nó, tham số value sẽ bằng với defaultValue đã được truyền tới createContext()
    ```javascript
    <MyContext.Consumer>
    {value => /* render gì đó dựa vào context value */}
    </MyContext.Consumer>
    ```
- Class.contextType: contextType là một thuộc tính của class được tạo bởi React.createContext()được dùng để lấy giá trị của context.
    ```javascript
    class MyClass extends React.Component {
        render() {
            let value = this.context;
        }
    }
    MyClass.contextType = MyContext;
    ```
- Context.displayName: Đặt tên cho Context, tên này sẽ được hiện thị trong DevTools
    ```javascript
    const MyContext = React.createContext(/* some value */);
    MyContext.displayName = 'MyDisplayName';
     
    <MyContext.Provider> // "MyDisplayName.Provider" in DevTools
    <MyContext.Consumer> // "MyDisplayName.Consumer" in DevTools
    ```
## Sử dụng Context trong ReactJS
- Khởi tạo object context bằng phương thức React.createContext(), sau đó chúng ta sẽ nhận được 1 object bao gồm các thuộc tính quan trọng như Provider và Consumer
- Sử dụng Provider bọc quanh các component, và truyền giá trị vào props value
- Thêm Consumer vào bất cứ đâu mà bạn muốn chia sẻ context miễn là ở bên trong Provider, bạn có thể lấy gía trị của context thông qua props.children
