Linked list:
-Linked list là một tập hợp chứa các node được liên kết với nhau, node sau chứa 1 link tới node kế tiếp.
Ưu điểm:
-Tiết kiệm bộ nhớ
-Thêm và xóa node nhanh
Nhược điểm:
-Tìm kiếm node chậm do phải duyệt từng node

Linked list tạo bằng JavaScript:
class Node {
    constructor(value, next = null){
        this.value = value
        this.next = next
    }
}
class LinkedList {
    constructor(){
        this.head = null
    }

    // Linked list methods here //
}