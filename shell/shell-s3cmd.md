## s3cmd命令

1. 基本使用
   1. 列出所有的bucket的所有对象:`s3cmd la`
   2. 列出当前账号下的所有bucket:`s3cmd ls`
   3. 建立新的bucket：`s3cmd mb s3://sholy`
   4. 上传文件到现有的bucket：`s3cmd put file1 file2 s3://sholy`
   5. 查看现有的bucket内容：`s3cmd ls s3://sholy/`
   6. 下载bucket中的文件：`s3cmd get s3://sholy/*.png`
   7. 删除bucket中的文件：`s3cmd del s3://sholy/*.png`
   8. 获取bucket中的信息：`s3cmd info s3://sholy`
   9. 删除现有的bucket：`s3cmd rb -r s3://sholy #-r表示删除文件夹` 
   10. 查看bucket大小：`s3cmd du s3://sholy`
   11. 文件拷贝：`s3cmd cp s3://bucket1/file s3://bucket2/file #-r 可以复制目录`
   12. 移动文件：`s3cmd cp s3://bucket1/file s3://bucket2/fil`

2. 复杂使用
    1. 上传文件夹：`s3cmd put [-r] dir1 s3://icyboy/some/path/`
    2. 同步：`s3cmd sync  ./  s3://icyboy/some/path/ #同步本地目录到s3目录`
    3. 同步：`s3cmd sync --dry-run --exclude '*.txt' --include 'dir2/*' . s3://icyboy/demo/ `