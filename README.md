/*****************************************************************************************
 * 免责声明 (Disclaimer)
 *****************************************************************************************
 * 1. 本软件（Kernel64Ark）为免费学习交流工具，作者仅提供软件本身，不提供任何形式的技术支持、
 *    质量保证或使用承诺，软件的稳定性、兼容性等均不做担保。
 *
 * 2. 因ARK工具的特殊性，使用本软件可能存在蓝屏、程序崩溃、系统异常等风险，进而导致数据丢失、
 *    设备损坏、业务中断等直接或间接损失。用户使用前必须备份所有重要数据，使用行为即视为
 *    自愿承担全部风险，作者对任何损失不承担任何赔偿责任。
 *
 * 3. 软件的著作权归作者所有，未经作者书面授权：
 *    - 禁止用于商业用途（包括但不限于有偿提供服务、捆绑销售、广告植入等）；
 *    - 禁止进行篡改、反向工程、破解、脱壳、分发破解版、二次封装等侵犯知识产权的行为。
 *
 * 4. 禁止将本软件用于任何非法或恶意用途，包括但不限于：
 *    - 作为病毒、木马、恶意程序的组件；
 *    - 破解网吧收费系统、软件授权保护、网络安全防护等；
 *    - 侵犯他人隐私、窃取数据、破坏计算机信息系统等违反《网络安全法》《刑法》等法律法规的行为。
 *    若违反本条，用户需自行承担全部法律责任，与作者无关。
 *
 * 5. 本软件仅限合法的学习交流场景使用，若用户使用本软件导致第三方侵权，应在收到侵权通知后
 *    24小时内停止使用并删除软件，作者不承担连带侵权责任。
 *
 * 6. 用户通过QQ（2907783620）或QQ群（703678829）反馈的BUG、建议，作者可自主决定是否修复
 *    或采纳，不构成必须履行的义务，不承诺修复时效。
 *
 * 7. 作者有权根据实际情况修改本免责声明，修改后的版本将通过上述QQ/QQ群或软件更新公告发布，
 *    用户继续使用软件即视为接受修改后的条款。
 *
 * 8. 本免责声明自用户首次使用软件之日起生效，未尽事宜均适用中华人民共和国相关法律法规。
 *****************************************************************************************
 * 反馈方式：QQ 2907783620 | QQ群 703678829
 * 欢迎反馈BUG及优化建议，感谢您的支持！
 *****************************************************************************************/

1.0.1.1:
1.ssdt 修复 增加检查inline hook + 恢复
2.ShadowSSDT 修复 增加检查inline hook + 恢复
3.idt 修复地址错误
4.新增内核钩子
5.新增文件系统+minifilter 移除的时候不卡顿
6.新增 Fsd 派发函数
7.新增 Keybd 派发函数
8.新增 I8024 派发函数
9.新增 Mouse 派发函数
10.新增 HalDispatchTable 的枚举
9.新增 Wdf01000 派发函数
10.新增 即插即用 PlugPlay 回调 
11.新增 反汇编窗口
12.ssdt and sssdt 增加重载后的地址
13.新增进程界面 显示进程树的效果  
14.新增启动项 Table
15.新增 服务 Table
16.新增 计划任务 Table
17.新增 进程 驱动 文件 菜单 检验数字签名
18.加了个应用层的简单注入



1.0.1.2:
1.增强进程枚举操作
2.增强驱动枚举操作
3.增强反汇编符号
4.使用共享内存+Event 通讯
5.监控全局
{
		case EventProcessCreate:    strOperation = _T("进程创建"); break;
		case EventProcessExit:      strOperation = _T("进程退出"); break;
		case EventProcessSuspend:   strOperation = _T("进程挂起"); break;
		case EventThreadCreate:     strOperation = _T("线程创建"); break;
		case EventThreadExit:       strOperation = _T("线程退出"); break;
		case EventDriverLoad:       strOperation = _T("驱动加载"); break;
		case EventDllLoad:          strOperation = _T("DLL加载"); break;
		case EventModuleUnload:     strOperation = _T("模块卸载"); break;
		case EventFileCreate:       strOperation = _T("文件创建"); break;
		case EventFileQueryDir:     strOperation = _T("目录查询"); break;
		case EventFileRead:         strOperation = _T("文件读取"); break;
		case EventFileWrite:        strOperation = _T("文件写入"); break;
		case EventRegKeyCreate:     strOperation = _T("注册表创建"); break;
		case EventRegKeyDelete:     strOperation = _T("注册表删除"); break;
		case EventNetworkConnect:   strOperation = _T("网络连接"); break;
		default:                    strOperation = _T("未知事件"); break;
}

6.下载多个符号文件 获取原始函数地址 检测挂钩
7.获取多个派发函数 获取原始函数地址 恢复挂钩
8.新增HalPrivateDispatchTable HalAcpiDispatchTable HalSubComponents 的枚举
9.修复软件下载符号失败 下载失败也可以从设置界面点击 然后关闭软件 注册表设置值进行替换
10.修复ssdt和sssdt 显示的函数名字错误 使用符号文件进行获取函数名字
11.新增 进程KernelCallbackTable 的枚举
12.新增 进程VAD //delete 
13.明天新增 进程窗口 热键 定时器 消息钩子 还有object   
14.考虑加个下载进度条 还有内核钩子  菜单 扫描符号表



1.0.1.3
1.内核-回调-加了个禁用函数
2.修复了线程 状态的显示
3.添加了个HalIommuDispatchTable
4.修复驱动加载失败错误码的显示
5.添加了个保护进程 
6.修复符号偶尔能加载 偶尔加载不了
7.修复了一些bug,减少内存的分配
8.反汇编器加了个编辑内核
9.加上WFP Filter
10.计划任务添加了菜单
11.加上WFP Object
12.加上过滤驱动 DPC IoTimer 功能的菜单
2025.12.7 






2026.1.21
1.0.1.4
1.添加了两个结束进程的按钮
2.修复反汇编蓝屏
3.添加文件句柄菜单
4.设置界面添加了个符号修改器
5.修复了ssdt名字显示错误的问题
6.进程-模块界面添加了菜单
7.添加了个阻止运行列表（结束进程后重新打开 打不开了）
8.添加了个应用层的apc dll注入
9.添加了个进程挂起计数检测
10.添加了个speedhack
11.注册表修改值 
12.计划任务加禁用  
13.应用层驱动加载器


2026.2.2
1.0.1.5
1.设置界面加了个符号下载(可在符号下载失败的时候换地址)
2.减少符号下载数量(之前20个符号)
3.结束进程可多选
4.设置界面加了个符号路径选择(针对已经下载符号的但是软件要求重下的)
5.修复界面缝隙大的问题 1920x1080 完美
6.修复反汇编蓝屏 
7.添加窗口保护 取消保护 三个值 关于反截屏的
| 值            | 宏                        | 含义                | 用途                            |
| ------------ | ------------------------ | ----------------- | ----------------------------- |
| `0x00000000` | `WDA_NONE`               | 无限制               | 默认值，窗口内容可被正常捕获（截图、录屏、远程桌面等）   |
| `0x00000001` | `WDA_MONITOR`            | 显示器亲和             | 窗口仅显示在主显示器上，阻止 GDI/DirectX 捕获 |
| `0x00000011` | `WDA_EXCLUDEFROMCAPTURE` | 排除捕获（Win10 2004+） | 完全阻止所有捕获，包括截图、录屏、缩略图、放大镜等     |
8.调整布局 解决之前缝隙大的问题
9.加强隐藏进程 过ydark opernark (进程退出必蓝)
10.新增应用层钩子界面 把进程菜单右键的进程钩子移动到这里了
11.应用层的代码加了个Zydis库 用来扫描进程钩子
12.加了个扫描进程钩子
13.扫描ntoskrnl.exe  钩子
14.移除进程热键  
15.移除消息钩子 
16.移除进程定时器  
17.检测inifityhook ssdt tab 弹窗 
18.加了个隐藏驱动(简单版)





1.0.1.6
1.加个进程伪装 
2.加个内存加载驱动 
3.把常见的内核注入加进去 1.远程线程注入  
5.进程内存添加 分配内存 释放内存 
6.模块界面添加隐藏模块  
7.各种irp菜单 
8.各种hal菜单 
9. PspCidTable 枚举隐藏进程
10.扫描隐藏驱动 
11.NtQueryVirtualMemory 遍历隐藏进程


1.0.1.7
1.修复bug 
2.扫描内存加载驱动 再驱动右键菜单设置 
3.进程界面加个应用层的内存加载dll 
4.修复了在win7 ssdt全错的结果 
5.DumpDriver
6.添加了个页表扫描(只有虚拟地址转物理地址了) 内核态(不能开监控,开了扫不了)
7.ssdt sssdt 界面只显示被hook的函数信息
8.隐藏进程只断链一个 断链线程蓝屏很快




1.0.1.8
1.加个进程权限 
2.加个驱动线程查看 
3.加个驱动IRP查看 
4.进程和文件加个MD5 SHA256 计算   
6.禁用全局监控 进程 线程 模块 开关 
7.页表查找加个HexDump+文件界面  HexDump 加 文件树 HexDump 
8.设置界面加了个DSE的开关（新加了个下载ci.dll的符号） 
9.检测内核隔离 HVCI 是否开启(开启后软件跑不了) 
10.加个线程栈回溯 Stack Walk  应用层实现 
11.修复 win11 24h2之后结构体变了 定时器 热键 消息钩子 都枚举不了 
12.网络界面加个菜单 
13.驱动界面加了个复制文件的菜单 
14.修复了快速切换的bug 导致程序崩溃 
15.HexDump添加修改 
16.回调界面加了个恢复配合之前的版本的Patch
17.修复枚举进程热键 vk 显示错误





1.0.1.9
1.添加个致谢名单  
2.添加个内核弹窗  
3.添加个infinityhook V(没提供接口 有空再继续搞)  test文件打不开 
4.文件过滤的动态补丁  
5.HexDump 加快速度 做到秒显示  
6.优化枚举进程	
7.扫描隐藏驱动特征码 不扫描r w x权限了  
8.系统回调补丁区分显示 		
9.HexDump加了个菜单 
10.添加了个热键Ctrl+C 复制一行 
11.Dump内核模块 简简单单dump了 没修复导入表 导出表 
12.修复读取大内存 0x50蓝屏 PAGE_FAULT_IN_NONPAGED_AREA 
13.加了个拷贝进程模块 
14.HexDump加了个应用层内存Dump  
15.添加了个Ctrl+F 查找 



1.0.2.0
1.修复 HexDump 进程内存容易蓝屏
2.修复 patch 容易蓝屏 (待测试)
3.修复枚举进程热键容易无效
4.修复枚举进程定时器容易无效
5.发布Release版本 (加了VMP后更稳定）
6.优化了界面显示
7.HexDump 内添加了 几个编码格式
8.移除内核钩子扫描 和 ntoskrnel钩子扫描 都是吃力不讨好的功能 还容易蓝
9.新加进程页表
10.使用多线程下载PDB符号文件(单核cpu还是下载的较慢)
11.进程Vad改用 VirtualQuery 查询
12.加强idt hook的检测



 
 
 
 
待加 解析NTFS的MFT表来搜索文件 x
待加 加了写特征码定位 一些系统在 软件启动后询问需要下载符号可以点击不下也能使用

https://learn.microsoft.com/zh-cn/windows-hardware/drivers/debugger/bug-check-0x109---critical-structure-corruption
https://www.vergiliusproject.com/kernels/x64/windows-7/sp1/_EPROCESS
https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-erref/596a1078-e883-4972-9bbc-49e60bebca55
https://learn.microsoft.com/en-us/windows/security/hardware-security/enable-virtualization-based-protection-of-code-integrity?tabs=security
https://learn.microsoft.com/en-us/windows/win32/api/winternl/nf-winternl-ntquerysysteminformation
https://www.unknowncheats.me/
https://hexrays.su/
https://r0keb.github.io/posts/PatchGuard-Internals/




