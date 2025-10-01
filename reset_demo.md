# Git Reset Demo

## Trạng thái trước khi reset:
- history.txt có 4 dòng: Dòng 1, Dòng 2, Dòng 4, Dòng 5
- Có các commit: Add line 5, Add line 4, Revert "Add line 3"

## 1. Reset --soft
```bash
git reset --soft HEAD~2
```
**Kết quả:**
- HEAD: quay về commit "Revert Add line 3"  
- Staging area: vẫn giữ thay đổi từ "Add line 4" và "Add line 5"
- Working directory: file vẫn có 4 dòng
- Dùng khi: muốn gộp commit hoặc sửa commit message

## 2. Reset --mixed (mặc định)
```bash
git reset --mixed HEAD~2
```
**Kết quả:**
- HEAD: quay về commit "Revert Add line 3"
- Staging area: bị xóa (unstaged)
- Working directory: file vẫn có 4 dòng
- Dùng khi: muốn unstage thay đổi nhưng giữ nội dung file

## 3. Reset --hard (NGUY HIỂM!)
```bash
git reset --hard HEAD~2
```
**Kết quả:**
- HEAD: quay về commit "Revert Add line 3"
- Staging area: bị xóa
- Working directory: file chỉ còn 2 dòng (mất Dòng 4, Dòng 5)
- Dùng khi: muốn xóa hoàn toàn thay đổi