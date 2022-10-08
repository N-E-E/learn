# topic
## vscode开发ros流程
参考：[参考](https://blog.csdn.net/g944468183/article/details/123759886)
- 创建一个工作空间文件夹并在下方创建一个src文件(名字不能改)
- 回到工作区执行catkin_make命令
- 使用vscode打开工作区，右键src执行create_catkin_pkg,根据提示输入包名、依赖库。这一步对应的是命令行执行相应命令
- 在src/包名/src中编写代码后，修改对应包下的cmake文件，在合适位置添加：
    ```cmake
    add_executable(velocity_publisher src/velocity_publisher)
    target_link_libraries(velocity_publisher ${catkin_LIBRARIES})
    ```
    注意，这一步一定不能修改成工作空间/src下的那个cmake，不然就寄了，原因是：[原因](https://blog.csdn.net/weixin_44741023/article/details/91467907)
- 在工作区目录下执行catkin_make
- 找到devel文件夹下的setup.bash并添加到环境变量，建议直接改bashrc里面的内容
