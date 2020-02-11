# apt 常用命令

| command               | func                                                        |
| --------------------- | ----------------------------------------------------------- |
| apt update            | 更新本地源缓存                                              |
| apt updrade           | 升级已安装软件                                              |
| apt list              | 列出本地仓库所有的软件包名                                  |
| apt list [package]    | 列出特定包名                                                |
| apt list --installed  | 列出已安装包名                                              |
| apt search [key]      | 根据关键字搜索                                              |
| apt show [package]    | 显示详细信息                                                |
| apt install [package] | 安装包                                                      |
| apt remove [package]  | 删除宝，但不删除配置文件，支持通配符                        |
| apt autoremove        | 卸载因安装软件自动安装的依赖，而现在又不需要的依赖包        |
| apt purge [package]   | 卸载包，同时删除相关配置文件。包名支持通配符                |
| apt clean             | 删除所有已下载的软件包                                      |
| apt autoclean         | 类似clean，但删除的是过期的包（即已不能下载或者是无用的包） |

