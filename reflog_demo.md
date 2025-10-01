# Git Reflog Demo

## Tình huống: 
Đã thực hiện `git reset --hard HEAD~2` và mất các commit "Add line 4" và "Add line 5"

## Git Reflog là gì?
- Reflog ghi lại tất cả thay đổi của HEAD
- Giúp khôi phục commit "đã mất" sau khi reset --hard
- Chỉ lưu trữ local, không push lên remote

## Các bước khôi phục:

### 1. Xem reflog
```bash
git reflog
```

Kết quả mẫu:
```
789abc HEAD@{0}: reset: moving to HEAD~2
abc123 HEAD@{1}: commit: Add line 5
def456 HEAD@{2}: commit: Add line 4  
789abc HEAD@{3}: revert: Revert "Add line 3"
0850f3f HEAD@{4}: commit: Add line 3
```

### 2. Khôi phục bằng checkout tạo nhánh mới
```bash
git checkout -b recovered abc123
```

### 3. Hoặc reset trực tiếp về commit cũ
```bash
git reset --hard abc123
```

### 4. Kiểm tra kết quả
```bash
git log --oneline
cat history.txt
```

## Lưu ý quan trọng:
- Reflog chỉ lưu trong 30-90 ngày (tùy cấu hình)
- Không thể khôi phục từ remote nếu chưa push
- Luôn cẩn thận với `reset --hard`