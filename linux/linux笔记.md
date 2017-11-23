### 批量重命名当前目录下的所有文件
> **将当前目录下所有文件的文件名中的 'home.' 替换为 'banner.'**  
> - 方法1： find . -exec rename home. banner. {} \;  
> - 方法2： rename -v home. banner. \*.\*  


### cp -f 在目标文件已存在时，复制仍会显示提示是否覆盖
> 系统在安装的时候使用了别名，alias cp='cp -i'，使用 \cp -f 或者修改系统别名配置均可解决问题