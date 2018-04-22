### SSH远程连接另一主机
```
ssh user_name@127.0.0.1
# 示例
ssh ubuntu@182.254.151.112
```

### 分支处理
# 放弃本分支修改
git stash
# 切换回master分支
git checkout master
# 删除本地分支
git branch -D ubuntu_dev
# 获取远程分支更新
git fetch
# 获取远程分支
git checkout -b ubuntu_dev origin/ubuntu_dev




### 常用操作
<table>
    <tr>
        <th>NO</th>
        <th>分类</th>
        <th>PS1 </th>
        <th>命令名</th>
        <th>用法及参数</th>
        <th>功能注解</th>
<th>对应章节</th>
    </tr>
    <tr><td>1</td><td>文件管理</td><td>#</td><td>ls</td><td>ls -a</td><td>列出当前目录下的所有文件，包括以.头的隐含文件</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>ls</td><td>ls -l或ll</td><td>列出当前目录下文件的详细信息</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>pwd</td><td>pwd</td><td>查看当前所在目录的绝对路经</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>cd</td><td>cd ..</td><td>回当前目录的上一级目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>cd</td><td>cd -</td><td>回上一次所在的目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>cd</td><td>cd ~ 或 cd</td><td>回当前用户的宿主目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>cd</td><td>cd /media/Ubuntu</td><td>跳转指定目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>cd</td><td>cd ~用户名</td><td>回指定用户的宿主目录</td><td></td></tr>
<tr><td>2</td><td>文件管理</td><td>#</td><td>mkdir</td><td>mkdir 目录名</td><td>创建一个目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>mkdir</td><td>mkdir –p</td><td>递归式去创建一些嵌套目录</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>rmdir</td><td>Rmdir 空目录名</td><td>删除一个空目录</td><td></td></tr>
<tr><td>3</td><td>文件管理</td><td>#</td><td>rm</td><td>rm 文件名 文件名</td><td>删除一个文件或多个文件</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>rm</td><td>rm -rf 非空目录名</td><td>递归删除一个非空目录下的一切，不让提式-f</td><td></td></tr>
<tr><td>4</td><td>文件管理</td><td>#</td><td>cat</td><td>cat文件名</td><td>一屏查看文件内容</td><td></td></tr>
<tr><td>5</td><td>文件管理</td><td>#</td><td>more</td><td>more文件名</td><td>分页查看文件内容</td><td></td></tr>
<tr><td>6</td><td>文件管理</td><td>#</td><td>less</td><td>less 文件名</td><td>可控分页查看文件内容</td><td></td></tr>
<tr><td>7</td><td>文件管理</td><td>#</td><td>grep</td><td>grep字符 文件名</td><td>根据字符匹配来查看文件部分内容</td><td></td></tr>
<tr><td>8</td><td>文件管理</td><td>#</td><td>mv</td><td>mv 路经/文件 /经/文件</td><td>移动相对路经下的文件到绝对路经下</td><td></td></tr>
<tr><td></td><td>文件管理</td><td>#</td><td>mv</td><td>mv 文件名 新名称</td><td>在当前目录下改名</td><td></td></tr>
<tr><td>9</td><td>文件管理</td><td>#</td><td>cp</td><td>cp /路经/文件 ./</td><td>移动绝对路经下的文件到当前目录下</td><td></td></tr>
<tr><td>10</td><td>文件管理</td><td>#</td><td>find</td><td>find 路经 -name “字符串”</td><td>查找路经所在范围内满足字符串匹配的文件和目录</td><td></td></tr>
<tr><td>11</td><td>文件管理</td><td>#</td><td>ln</td><td>ln 源文件 链接名</td><td>创建当前目录源文件的硬链接</td><td></td></tr>
<tr><td></td><td>ln /home/test /usr/test1</td><td></td><td></td><td>在/usr下建立/home/test的硬链接</td><td></td><td></td></tr>
<tr><td>12</td><td>文件管理</td><td>#</td><td>ln</td><td>Ln -s a b</td><td>创建当前目录下a的符号链接b</td><td></td></tr>
<tr><td>13</td><td>文件管理</td><td>#</td><td>touch</td><td>touch file1 file2</td><td>创建两个空文件</td><td></td></tr>
<tr><td>14</td><td>磁盘管理</td><td>#</td><td>df</td><td>df</td><td>用于报告文件系统的总容量，使用量，剩余容量。</td><td></td></tr>
<tr><td>15</td><td>磁盘管理</td><td>#</td><td>du</td><td>du -b /home</td><td>查看目前/HOME目录的容量(k)及子目录的容量(k)。</td><td></td></tr>
<tr><td>16</td><td>磁盘管理</td><td>#</td><td>fdisk</td><td>fdisk -l</td><td>查看系统分区信息</td><td></td></tr>
<tr><td>17</td><td>磁盘管理</td><td>#</td><td>fdisk</td><td>fdisk /dev/sdb</td><td>为一块新的SCSI硬盘进行分区</td><td></td></tr>
<tr><td>18</td><td>磁盘管理</td><td>#</td><td>mkfs.ext3</td><td>Mkfs.ext3 /dev/sdb1</td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td>mkfs.ext2</td><td>Mkfs.ext2/dev/sdb2</td><td></td><td></td></tr>
<tr><td>19</td><td>磁盘管理</td><td>#</td><td>mount</td><td>mount -t 文件系统类型 设备路经 访问路经</td><td></td><td></td></tr>
<tr><td></td><td>磁盘管理</td><td>#</td><td></td><td>文件系统类型</td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>Iso9660</td><td>光驱文件系统</td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>vfat</td><td>Fat文件系统(windows)</td><td></td></tr>
<tr><td></td><td>挂载光驱</td><td>#</td><td>mount –t iso9660 /dev/cdrom /mnt/cdrom</td><td></td><td></td><td></td></tr>
<tr><td></td><td>挂载FAT</td><td>#</td><td>mount –t vfat /dev/hda5 /mnt/cdrom</td><td></td><td></td><td></td></tr>
<tr><td>17</td><td>磁盘管理</td><td>#</td><td>Umount /mnt/cdrom</td><td></td><td></td><td></td></tr>
<tr><td>18</td><td>文件权限</td><td>#</td><td>chmod</td><td>chmod u+s file</td><td>为file的属主加上特殊权限</td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>chmod g+r file</td><td>为file的属组加上读权限</td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>chmod o+w file</td><td>为file的其它用户加上写权限</td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td>chmod a-x file</td><td>为file的所有用户减去执行权限</td><td></td></tr>
<tr><td></td><td>chmod 765 file 为file的属主设为完全权限，属组设成读写权，其它用户具有读和执心权限</td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td>19</td><td>文件权限</td><td>#</td><td>chown</td><td>chown root /home</td><td>把/home的属主改成root用户</td><td></td></tr>
<tr><td>20</td><td>文件权限</td><td>#</td><td>chgrp</td><td>chgrp root /home</td><td>把/home的属组改成root组</td><td></td></tr>
<tr><td>21</td><td>打印管理</td><td>#</td><td>redhat-config-printer-tui</td><td></td><td>进入安装打印机界面</td><td></td></tr>
<tr><td>22</td><td>打印管理</td><td>#</td><td>lp</td><td>lp –d hptr file</td><td>打印file到hptr的打印机上</td><td></td></tr>
<tr><td>23</td><td>打印管理</td><td>#</td><td>lpq</td><td>Lpq –P 打印机名</td><td>查看打印机的状态</td><td></td></tr>
<tr><td>24</td><td>打印管理</td><td>#</td><td>lprm</td><td>Lprm –P 打印机名 a</td><td>删除打印机内的打印作业</td><td></td></tr>
<tr><td>25</td><td>打印管理</td><td>#</td><td>disable</td><td>Disable –r “changing paper” HPtr</td><td></td><td></td></tr>
<tr><td>26</td><td>打印管理</td><td>#</td><td>enable</td><td>Enable HPtr</td><td></td><td></td></tr>
<tr><td>27</td><td>用户管理</td><td>#</td><td>useradd</td><td>Useradd</td><td></td><td></td></tr>
<tr><td>28</td><td>用户管理</td><td>#</td><td>groupadd</td><td>Groupadd 组名</td><td></td><td></td></tr>
<tr><td>29</td><td>用户管理</td><td>#</td><td>passwd</td><td>Passwd 用户名</td><td></td><td></td></tr>
<tr><td>30</td><td>用户管理</td><td>#</td><td>Passwd -d</td><td>Passwd -d用户名</td><td></td><td></td></tr>
<tr><td>31</td><td>用户管理</td><td>#</td><td>Passwd -l</td><td>Passwd -l用户名</td><td></td><td></td></tr>
<tr><td>32</td><td>用户管理</td><td>#</td><td>Passwd -u</td><td>Passwd -u用户名</td><td></td><td></td></tr>
<tr><td>33</td><td>用户管理</td><td>#</td><td>Passwd -S</td><td>Passwd -S用户名</td><td></td><td></td></tr>
<tr><td>34</td><td>用户管理</td><td>#</td><td>Usermod -l</td><td>Usermod -l 新用户名 老用户名</td><td></td><td></td></tr>
<tr><td>35</td><td>用户管理</td><td>#</td><td>Usermod -L</td><td>Usermod -L 要锁定用户名</td><td></td><td></td></tr>
<tr><td>36</td><td>用户管理</td><td>#</td><td>Usermod -U</td><td>Usermod –U解锁用户名</td><td></td><td></td></tr>
<tr><td>37</td><td>用户管理</td><td>#</td><td>Usermod -u</td><td>Usermod –u 501用户名</td><td></td><td></td></tr>
<tr><td>38</td><td>用户管理</td><td>#</td><td>Userdel</td><td>Userdel–r 用户名</td><td></td><td></td></tr>
<tr><td>39</td><td>用户管理</td><td>#</td><td>Groupmod -n</td><td>Groupmod –n新用户名 老用户名</td><td></td><td></td></tr>
<tr><td>40</td><td>用户管理</td><td>#</td><td>Groupmod -g</td><td>Groupmod –g 501 组名</td><td></td><td></td></tr>
<tr><td>41</td><td>用户管理</td><td>#</td><td>groupdel</td><td>Groupdel组名 先应删它的用户</td><td></td><td></td></tr>
<tr><td>42</td><td>用户管理</td><td>#</td><td>gpasswd -a</td><td>gpasswd -a 用户名 组名</td><td></td><td></td></tr>
<tr><td>43</td><td>用户管理</td><td>#</td><td>Id</td><td>id 用户名</td><td></td><td></td></tr>
<tr><td>44</td><td>软件管理</td><td>#</td><td>rpm -qa</td><td>rpm –qa | less</td><td></td><td></td></tr>
<tr><td>45</td><td>软件管理</td><td>#</td><td></td><td>rpm –qa | grep ftp</td><td></td><td></td></tr>
<tr><td>46</td><td>软件管理</td><td>#</td><td>rpm -q</td><td>rpm -q 已安装的RPM包</td><td></td><td></td></tr>
<tr><td>47</td><td>软件管理</td><td>#</td><td></td><td>rpm -q telnet-server</td><td></td><td></td></tr>
<tr><td>48</td><td>软件管理</td><td>#</td><td>rpm -qi</td><td>rpm –qi 软件包名称</td><td></td><td></td></tr>
<tr><td>49</td><td>软件管理</td><td>#</td><td>rpm -ql</td><td>rpm –ql软件包名称</td><td></td><td></td></tr>
<tr><td>50</td><td>软件管理</td><td>#</td><td>rpm -qf</td><td>rpm –qf软件包名称</td><td></td><td></td></tr>
<tr><td>51</td><td>软件管理</td><td>#</td><td>rpm -qp</td><td>rpm –qp软件包全名</td><td></td><td></td></tr>
<tr><td>52</td><td>软件管理</td><td>#</td><td>rpm -e</td><td>rpm –e 软件包名称</td><td></td><td></td></tr>
<tr><td>53</td><td>软件管理</td><td>#</td><td>rpm -U</td><td>rpm –Uvh软件包全名</td><td></td><td></td></tr>
<tr><td>54</td><td>软件管理</td><td>#</td><td>rpm -ivh</td><td>rpm –ivh 软件包全名</td><td></td><td></td></tr>
<tr><td>55</td><td>软件管理</td><td>#</td><td>rpm -V</td><td>rpm –V软件包名称</td><td></td><td></td></tr>
<tr><td>56</td><td>软件管理</td><td>#</td><td>tar</td><td>-c 创建包 –x 释放包 -v 显示命令过程 –z 代表压缩包</td><td></td><td></td></tr>
<tr><td>57</td><td>软件管理</td><td>#</td><td>tar -cf</td><td>tar –cvf benet.tar /home/benet</td><td></td><td></td></tr>
<tr><td>58</td><td>软件管理</td><td>#</td><td>tar -czf</td><td>tar –zcvf benet.tar.gz /mnt</td><td></td><td></td></tr>
<tr><td>59</td><td>软件管理</td><td>#</td><td>tar –tf</td><td>tar –tf benet.tar</td><td></td><td></td></tr>
<tr><td>60</td><td>软件管理</td><td>#</td><td>tar –tzf</td><td>tar –tf benet.tar.gz</td><td></td><td></td></tr>
<tr><td>61</td><td>软件管理</td><td>#</td><td>tar –xf</td><td>tar –xf benet.tar</td><td></td><td></td></tr>
<tr><td>62</td><td>软件管理</td><td>#</td><td>tar –zxvf</td><td>tar –zxvf benet.tar.gz</td><td></td><td></td></tr>
<tr><td>63</td><td>软件管理</td><td>#</td><td>tar -jxvf</td><td>tar –jxvf benet.tar.bz2</td><td></td><td></td></tr>
<tr><td>64</td><td>软件管理</td><td>#</td><td>diff</td><td>diff file1 file2 > 补丁名.patch</td><td></td><td></td></tr>
<tr><td>65</td><td>软件管理</td><td>#</td><td>diff</td><td>diff file1 file2</td><td></td><td></td></tr>
<tr><td>66</td><td>软件管理</td><td>#</td><td>Patch</td><td>Patch</td><td></td><td></td></tr>
<tr><td>67</td><td>软件管理</td><td>#</td><td>./configure 必须在已解压目录下</td><td></td><td></td><td></td></tr>
<tr><td>68</td><td>软件管理</td><td>#</td><td>make</td><td></td><td></td><td></td></tr>
<tr><td>69</td><td>软件管理</td><td>#</td><td>make install</td><td></td><td></td><td></td></tr>
<tr><td>70</td><td>启动管理</td><td>#</td><td>reboot</td><td></td><td></td><td></td></tr>
<tr><td>71</td><td>启动管理</td><td>#</td><td>Halt</td><td></td><td></td><td></td></tr>
<tr><td>72</td><td>启动管理</td><td>#</td><td>runlevel</td><td></td><td></td><td></td></tr>
<tr><td>73</td><td>启动管理</td><td>#</td><td>Init [0123456]</td><td></td><td></td><td></td></tr>
<tr><td>74</td><td>启动管理</td><td>#</td><td>Chkconfig –-list [服务名称]</td><td></td><td></td><td></td></tr>
<tr><td>75</td><td>启动管理</td><td>#</td><td>Chkconfig –-level <运行级> <服务名> on|off|set</td><td></td><td></td><td></td></tr>
<tr><td>76</td><td>启动管理</td><td>#</td><td>Chkconfig <服务名> on|off|set</td><td></td><td></td><td></td></tr>
<tr><td>77</td><td>进程管理</td><td>#</td><td>Top动态</td><td></td><td></td><td></td></tr>
<tr><td>78</td><td>进程管理</td><td>#</td><td>程序名 &</td><td></td><td></td><td></td></tr>
<tr><td>79</td><td>进程管理</td><td>#</td><td>fg</td><td></td><td></td><td></td></tr>
<tr><td>80</td><td>进程管理</td><td>#</td><td>bg</td><td></td><td></td><td></td></tr>
<tr><td>81</td><td>进程管理</td><td>#</td><td>renice</td><td></td><td>把180号进程的优先级加1</td><td></td></tr>
<tr><td>82</td><td>进程管理</td><td>#</td><td>kill</td><td></td><td>终止某个PID进程</td><td></td></tr>
<tr><td>83</td><td>进程管理</td><td>#</td><td>at</td><td></td><td>指定三天后下午5:00执行/bin/ls</td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td>84</td><td>进程管理</td><td>#</td><td>crontab</td><td></td><td>用VI的形式来编辑自动周期性任务</td><td></td></tr>
<tr><td>85</td><td>进程管理</td><td>#</td><td>crontab</td><td></td><td>查看自动周期性任务</td><td></td></tr>
<tr><td>86</td><td>进程管理</td><td>#</td><td>crontab</td><td></td><td>删除自动周期性任务</td><td></td></tr>
<tr><td>87</td><td>进程管理</td><td>#</td><td>crond</td><td></td><td></td><td></td></tr>
<tr><td></td><td>下载</td><td></td><td>wget –c https://........</td><td></td><td></td><td></td></tr>
<tr><td></td><td>马上启动自动周期性服务</td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td>实现磁盘配额</td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
<tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>

</table>

 