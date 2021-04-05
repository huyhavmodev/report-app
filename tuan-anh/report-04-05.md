Binary search tree:
- Là một data structure cơ bản, chứa tập hợp các node 
có những đặc điểm sau:
+ Mỗi node chỉ chứa tối đa 2 node con
+ Giá trị node con bên phải nhỏ hơn node cha 
+ Giá trị node con bên trái lớn hơn node cha
- Các phương thức duyệt cây BST thường gặp:
+ Pre-order Traversal: duyệt các node cha trước theo thứ tự 
từ trái sang phải
+ In-order Traversal: duyệt từ các node con trái -> node cha
-> node con bên phải
+ Post-order Traversal: duyệt từ các node con trái -> node con 
phải -> node cha