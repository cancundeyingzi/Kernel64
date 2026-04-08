# Kernel64Ark

## 免责声明 (Disclaimer)

> 1. 本软件（Kernel64Ark）为免费学习交流工具，作者仅提供软件本身，不提供任何形式的技术支持、质量保证或使用承诺，软件的稳定性、兼容性等均不做担保。
> 
> 2. 因ARK工具的特殊性，使用本软件可能存在蓝屏、程序崩溃、系统异常等风险，进而导致数据丢失、设备损坏、业务中断等直接或间接损失。用户使用前必须备份所有重要数据，使用行为即视为自愿承担全部风险，作者对任何损失不承担任何赔偿责任。
> 
> 3. 软件的著作权归作者所有，未经作者书面授权：
>    - 禁止用于商业用途（包括但不限于有偿提供服务、捆绑销售、广告植入等）；
>    - 禁止进行篡改、反向工程、破解、脱壳、分发破解版、二次封装等侵犯知识产权的行为。
> 
> 4. 禁止将本软件用于任何非法或恶意用途，包括但不限于：
>    - 作为病毒、木马、恶意程序的组件；
>    - 破解网吧收费系统、软件授权保护、网络安全防护等；
>    - 侵犯他人隐私、窃取数据、破坏计算机信息系统等违反《网络安全法》《刑法》等法律法规的行为。
>    若违反本条，用户需自行承担全部法律责任，与作者无关。
> 
> 5. 本软件仅限合法的学习交流场景使用，若用户使用本软件导致第三方侵权，应在收到侵权通知后24小时内停止使用并删除软件，作者不承担连带侵权责任。
> 
> 6. 用户通过QQ（2907783620）或QQ群（703678829）反馈的BUG、建议，作者可自主决定是否修复或采纳，不构成必须履行的义务，不承诺修复时效。
> 
> 7. 作者有权根据实际情况修改本免责声明，修改后的版本将通过上述QQ/QQ群或软件更新公告发布，用户继续使用软件即视为接受修改后的条款。
> 
> 8. 本免责声明自用户首次使用软件之日起生效，未尽事宜均适用中华人民共和国相关法律法规。

**反馈方式：**
* QQ：2907783620
* QQ群：703678829
* 欢迎反馈BUG及优化建议，感谢您的支持！

---

## 更新日志

### 1.0.1.1
1. ssdt 修复 增加检查inline hook + 恢复
2. ShadowSSDT 修复 增加检查inline hook + 恢复
3. idt 修复地址错误
4. 新增内核钩子
5. 新增文件系统+minifilter 移除的时候不卡顿
6. 新增 Fsd 派发函数
7. 新增 Keybd 派发函数
8. 新增 I8024 派发函数
9. 新增 Mouse 派发函数
10. 新增 HalDispatchTable 的枚举
11. 新增 Wdf01000 派发函数
12. 新增 即插即用 PlugPlay 回调 
13. 新增 反汇编窗口
14. ssdt and sssdt 增加重载后的地址
15. 新增进程界面 显示进程树的效果  
16. 新增启动项 Table
17. 新增 服务 Table
18. 新增 计划任务 Table
19. 新增 进程 驱动 文件 菜单 检验数字签名
20. 加了个应用层的简单注入

### 1.0.1.2
1. 增强进程枚举操作
2. 增强驱动枚举操作
3. 增强反汇编符号
4. 使用共享内存+Event 通讯
5. 监控全局
   ```cpp
   {
       case EventProcessCreate:   strOperation = _T("进程创建"); break;
       case EventProcessExit:     strOperation = _T("进程退出"); break;
       case EventProcessSuspend:  strOperation = _T("进程挂起"); break;
       case EventThreadCreate:    strOperation = _T("线程创建"); break;
       case EventThreadExit:      strOperation = _T("线程退出"); break;
       case EventDriverLoad:      strOperation = _T("驱动加载"); break;
       case EventDllLoad:         strOperation = _T("DLL加载"); break;
       case EventModuleUnload:    strOperation = _T("模块卸载"); break;
       case EventFileCreate:      strOperation = _T("文件创建"); break;
       case EventFileQueryDir:    strOperation = _T("目录查询"); break;
       case EventFileRead:        strOperation = _T("文件读取"); break;
       case EventFileWrite:       strOperation = _T("文件写入"); break;
       case EventRegKeyCreate:    strOperation = _T("注册表创建"); break;
       case EventRegKeyDelete:    strOperation = _T("注册表删除"); break;
       case EventNetworkConnect:  strOperation = _T("网络连接"); break;
       default:                   strOperation = _T("未知事件"); break;
   }
