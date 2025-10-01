# So sánh Revert vs Reset

## Git Revert
- **Mục đích:** Tạo commit mới đảo ngược thay đổi
- **An toàn:** ✅ Không làm mất lịch sử
- **Team work:** ✅ An toàn khi đã push lên remote
- **Cách hoạt động:** Tạo commit mới với thay đổi ngược lại

**Ví dụ:**
```bash
git revert HEAD        # Revert commit cuối
git revert abc123      # Revert commit cụ thể
```

## Git Reset

### Reset --soft
- **Mục đích:** Di chuyển HEAD, giữ thay đổi trong staging
- **Dùng khi:** Muốn gộp commit, sửa commit message
```bash
git reset --soft HEAD~1
```

### Reset --mixed (mặc định)  
- **Mục đích:** Di chuyển HEAD, unstage thay đổi
- **Dùng khi:** Muốn sửa lại những gì sẽ commit
```bash
git reset HEAD~1
git reset --mixed HEAD~1  # Tương đương
```

### Reset --hard
- **Mục đích:** Di chuyển HEAD, xóa tất cả thay đổi
- **NGUY HIỂM:** ❌ Có thể mất dữ liệu
- **Dùng khi:** Muốn bỏ hoàn toàn thay đổi
```bash
git reset --hard HEAD~1
```

## Khi nào dùng gì?

| Tình huống | Nên dùng |
|------------|----------|
| Đã push lên remote | **Revert** |
| Chưa push, muốn sửa commit message | **Reset --soft** |
| Chưa push, muốn unstage | **Reset --mixed** |
| Chưa push, muốn xóa hết | **Reset --hard** |
| Làm việc nhóm | **Revert** |
| Làm việc cá nhân | **Reset** |

## Reflog - Cứu cánh cuối cùng
```bash
git reflog                    # Xem lịch sử HEAD
git checkout -b backup <hash> # Khôi phục an toàn
git reset --hard <hash>       # Khôi phục trực tiếp
```