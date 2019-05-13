python解压zip错误解决

# _*_ coding=utf-8 _*_
# 导入zipfile库
import zipfile
zFile = zipfile.ZipFile("H:/Workspace/python2.7/test.zip")
# 以只读模式打开zip压缩文件
file = open("H:/Workspace/python2.7/test.txt", "r")
for line in file.readlines():
    # 过滤空格
    password = line.strip('\n')
    # 异常处理
    try:
        zFile.extractall(pwd=password)
        print "password:" + password
        exit(0)
    except Exception, error:
        print error
        
确认密码正确的情况下，仍旧提示：
  ('Bad password for file', <zipfile.ZipInfo object at 0x0000000002C064C8>)
  ('Bad password for file', <zipfile.ZipInfo object at 0x0000000002C064C8>)
  ('Bad password for file', <zipfile.ZipInfo object at 0x0000000002C064C8>)
  ('Bad password for file', <zipfile.ZipInfo object at 0x0000000002C064C8>)
  ('Bad password for file', <zipfile.ZipInfo object at 0x0000000002C064C8>)
  
可能原因：
  查看是否为WinRAR压缩。WinRAR压缩使用私有加密算法
  
