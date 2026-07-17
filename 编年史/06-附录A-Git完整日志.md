# 附录 A：Git 完整日志

> 编年史 · 附录 A · v1（130 commits）+ v2（893 commits）

---

## v1 — math_platform（130 commits）

时间段：2026-06-21 ~ 2026-06-27

```
0d56d84  chore: init repository with .gitignore
8d3a101  feat: initial commit - 章鱼智学 (math_platform) full codebase
59b434c  security: harden Django settings, Nginx config, and system
f21c110  feat: UI优化 — 访客作业、学生首页改版、品牌名章鱼智学、作业进度真实化
ecf411f  feat: add error pages, logging, and reduce workers
a63156a  feat: 教师控制台 — 一站式布置作业、作业列表、卡片缺失检测、批量可见性
2c4dea4  chore: 教师控制台首页增加组卷PDF入口
54ec448  feat: 组卷系统重构 — 教师组卷界面+PDF引擎(支持中文/Markdown/LaTeX/配图/双版本)
acaa7fd  fix: 组卷功能 — 修复PDF下载(前端提交方式改为多input同名字段)
274fd84  fix: PDF download broken — three root causes resolved
d36bdcc  fix: PDF generation — fonts, LaTeX rendering, images, tag nesting
cb5b285  feat: 替换为 XeLaTeX PDF 渲染引擎
4ae6770  fix: XeLaTeX nonstopmode + 反斜杠归一化 + #转义
7c0ffb1  建立分层测试体系: 单元测试34个+集成测试48个+E2E场景10个, 共92个测试全部通过
9477c70  fix: 题号、表格、图片尺寸 + 新增原卷下载模块
3295c33  修复：题号从question_number取；Markdown表格→LaTeX转换；图片缩小到0.32\textwidth
7f24b52  修复：distinct()查询性能问题——添加.order_by()清除默认排序
798133e  修复：带圈数字①②③在PDF中缺失——用\xeCJKDeclareCharClass声明为CJK字符
0a733f5  修复：表格最后一行丢失；罗马数字缺失；去掉题头总分显示
7ca9136  init: 从服务器迁移本地开发环境
cce31d6  fix: 添加STATIC_ROOT/MEDIA_ROOT配置，清理重复的静态文件设置
450ebbc  chore: 测试自动部署链路
d340023  fix: 测试修复+Windows兼容+环境标记
be3bf65  fix: PDF 模板字体 fallback，本地 PDF 编译正常
1075387  feat: 解题页 E2E 测试 + 自检命名修正
021d65d  chore: 忽略 SQLite WAL 临时文件
70c51a8  fix: 选填题概念标签可点击打开知识卡片
57cf74c  fix: 解题页 tag 步骤渲染崩溃导致知识卡片不显示
d985f56  fix: 回退概念标签误改，保持纯文本展示
8bc4eef  feat: 前端数据契约测试 + 自检渲染检测组 + skill 检查清单
5cea374  fix: 解题模式配图过大 + 概念标签位置上移
bd1c7f2  fix: smartBack 竞态条件导致 history.back() 被覆盖
8ccd6d2  feat: JS 单元测试体系（smartBack/renderStepContent/canGoRight 等）
6a0bff8  fix: 继续做题→跳到第一个未做题；完成状态基于步骤数
11b799b  feat: 讲义底部展开按钮+↑↓控制+callout卡片样式+s-btn统一
1dba27e  chore: 刷新style.css缓存版本号
c96f90f  fix: s-btn 样式提取为通用类，讲义页按钮生效
958584f  feat: Course.title_suffix + Document.display_title 自动编号前缀
7e5123d  统一完成状态判定：废弃 completed_question_ids 字段，全部基于 Feedback 表实时计算
dc2de95  feat: 讲义阅读器 🖨️ 打印当前页PDF按钮
491b033  学生端完成状态显示统一：部分正确→进行中📝，推荐页完成标记不限snapshot_mode
b2653a1  教师端详情页拆双列（完成+正确性）；admin首页加教师控制台链接
c8d4f0a  PDF检测系统：check_pdf_all命令 + PdfTester单元测试 + 自检K17 + GROUP_COUNTS修正
212bb8f  修复解题模式假完成bug + 做题历史统一完成判定
3f7ff64  补非线性路径测试：不选反馈再进/部分反馈再进/选填/匿名/覆盖/连续访问
cfb2514  自检不依赖已有student账户：改为创建临时账户并自动清理
b559271  自检全函数改为临时创建账户：不依赖任何已有账号
67b0edc  修正pdffonts列解析（固定列宽） + 编译健康度阈值20s→60s（适配服务器2C2G）
285ad72  修复：移除 \IfFontExistsTF 条件检测，直接设置 Noto/Liberation 字体
5df4916  修复pdffonts列解析：用表头定位列偏移
7991724  修复：字体检测兼容FandolSong + pdffonts列解析用header定位
3b97463  集成 django-reversion：A 级 Model 通过 VersionAdmin 实现 admin 版本历史与回滚
41e1ff2  自检页：render/heavy 改为手动点击运行，不自动执行
11bf774  自检修复: 分组调整(heavy+release手动,render自动) + 集中清理泄漏数据
df8432a  自检: 将所有PDF编译测试(K6/K7/K14)移至heavy组(手动); release组恢复自动
7a97274  自检: 额外将D3/J1(组卷PDF触发编译)也从admin/hybrid移至heavy
63e486c  自检: render改为自动(非PDF), 仅heavy保留手动
488b65b  删除 teacher app，作业进度表搬迁到 AssignmentAdmin
e7ad7f4  教师角色名称改为助教：Admin过滤器/列显示/批量操作、模型verbose_name、模板显示
e28bd6a  修复自检系统：移除已删除的Exam/ExamQuestionOrder模型引用
53059f4  讲义底部改智能箭头+评分弹窗改两行布局；CSS缓存版本更新
00d4d83  评分范围改0-10（修复12345678910字符串迭代bug+模型choices+服务端验证）
0ce682c  修复二次评分按钮disabled不重置
cc09948  section_order改为JSONField存列表[子问,解法,步序]；display_label选填题显示；反馈数据体现层级
7723fb3  批量修改：推荐排除改用完成状态统一判定；知识卡片slug→name；admin json.loads bug修复
4fa0ddd  wip
7e4b190  知识卡片类别 choices 精简为仅有流程和定理
8dd5aed  PDF 测试管线修复+自检整合
2b56d9f  权限系统重构：Course可见性+RBAC角色组+Assignment关联课程
e5d900a  增加批量分组/设置课程 Action，去除作业独立可见性
83c82d3  作业编辑页去掉学生分组字段
288ca53  作业编辑页去掉学生选择，改为按组分派；同时支持按组和个人可见
2d30ffe  作业可见性完全继承课程，去掉个人分配逻辑
4303e17  作业编辑页彻底去掉学生和分组字段
16b0695  邀请码生成加碰撞检查；修复注册测试
320e87e  邀请码生成改进：InvitationCode页带中间页，User页生成保留
493bb30  积分横幅统一自动消失（base.html JS 3.5s 淡出）
e314497  修复：积分流水返回按钮改用 smartBack（不重新加载首页）
3f69bdb  修复：做题积分 Decimal + float 类型错误，改用 Decimal 计算（向下保留一位小数）
c3a987e  修复：0积分不报错；解题页显示所得积分；新增积分测试（32passed）
51a4d39  修复：SQLite 写锁导致积分丢失（WAL模式+timeout+API重试）
b9131b9  修复：claim API 不兼容 FormData（JS 发 FormData，API 只收 JSON）
4b7ef32  feat: 个性化组卷功能 - CustomExam模型/选题算法/6个页面/PDF连续编号
8b20aa2  fix: 保存POST带题目ID/算法调优/LaTeX渲染/按钮文字/列表去操作按钮
a5536ee  fix: 预览视图传入question_ids_json/新增12个端到端测试
1f9475d  fix: 选题算法中档按距高考平均值排序 + 调优步骤
d4015d7  feat: 极端情况放宽+提示消息/选题算法调优
46ac5ba  fix: 知识点过滤/已做完不放宽，尊重学生选择留空缺
63a47d8  fix: create.html 保存表单数据到sessionStorage供换一套使用
7ffe560  权限精简：Course 去掉 allowed_groups，改用 students 直连学生；清理空白平行组
359a104  删 Assignment.groups 字段；Admin 后台按语义分组（用户/课程/题目/反馈）
a709264  新增 StudentGroup 模型；Course 恢复 allowed_groups(M2M→StudentGroup)；Admin 分组更新
294c438  StudentGroup/Course 双向关联：列表页显示对方关联，编辑页可双向配置
d8b7504  题目预览页标题：管理员预览→题目预览（个性化组卷也访问此页面）
31142f1  管理员后台：批量赠送积分 Action（含积分流水记录）
32b0d52  修复作业到解题页的权限路由+preview零授权+组卷链接改solve
0c331f3  首页待办作业使用 get_visible_assignments，与作业列表/详情页权限一致
1fdef09  解题页退出改下一题+作业上下文传参
c1642c0  remove temp script
f5111f9  布置作业表单新增「所属课程」下拉选择
652ade5  管理后台快捷操作侧边栏补全：原卷下载、难度统计、系统自检
f6446a3  移除意外跟踪的 _srv_fulltest.py
59f2617  gitignore 忽略 _srv_fulltest.py
b35f014  fix: 管理后台快捷链接 URL name 错误修正
9c6a236  fix: 管理后台侧边栏去掉重复 content-related ID，确保快捷操作按钮可见
b0ff157  自检代码修复：删除已废弃的 Exam/teacher 检查，修正 slug/doc_type 等字段名错误
17782aa  组卷历史预览页显示学生做题状态（已完成/进行中/未做）
f13d2db  Selfcheck v2: 基于正确性验证的全新自检系统，setup→测试→teardown 生命周期
6728a9a  Fix BOM + escaped quotes in selfcheck.py, remove temp files
01df7bc  Fix selfcheck.py: complete content restored via PowerShell heredoc
3ec5f43  Selfcheck v2: 71/71 all green, fix passwords/fields/IC length/nav checks/backend/session
e02dbef  Fix selfcheck view: restore return render that was lost in push
62f169b  Selfcheck: auto-setup if fixtures missing
b92643b  修复管理员预览页上一题/下一题导航链接：硬编码的 /admin-preview/{{pk}}/ 改为 {% url 'question_preview' pk %}
c3e2d0e  新增审计日志模块：注册流程+Admin角色变更双轨日志
b4a4024  GroupAdmin编辑页增加组内用户多选
e89000a  Flutter Phase0 API: 16个端点(auth/questions/cards/assignments/lectures)
edcd8af  Flutter: auto checkin + register API
2083d9e  feat: 新增 flutter_home_stats API 首页学习统计端点
3156d2e  fix: urls.py 语法修复(逗号)
454be74  feat: 推荐API添加completion_status + 组卷API端点
91c7db2  fix: 新增 custom_exam_api.py
5d7b2df  feat: 快照API+组卷删除+custom_exam_api delete视图
03014ee  fix: import require_POST
5ea2b74  Fix custom exam API + add create endpoint
6633773  feat: 组卷创建/预览/保存 JSON API
a464ddf  fix: remove stale url ref flutter_custom_exam_create
752e86b  Docs: selfcheck v2 redesign summary
005c108  修复Markdown表格PDF渲染：正则允许对齐行中空格 + Q210数据补对齐行
```


---

## v2 — zhangyuzhixue_app_v2（893 commits）

时间段：2026-07-02 ~ 2026-07-17

```
52eacdc  初始项目骨架：flutter create + 按设计稿新建空文件结构
ef134aa  feat: 新增 repositories 数据仓库层，读取静默mock / 写入Toast提示
3e0e52a  设计规范：更新三、本地数据库层，按 repositories 逐一对应
d6e8141  设计规范：更新三、本地数据库层，按 repositories 逐一对应
c7ba21b  合并 flutter_app 项目至主仓库（保留完整提交历史）
725658b  添加 .gitignore（排除 flutter_app 构建产物和 Django 项目）
e3c8305  设计规范：新增登录/注册页面（§0），补充 Flutter 端的认证入口
49b93b3  设计规范：将交互层（§1-§8 + 全局备注）从条目列表改为表格格式
489d7d1  设计规范：统一交互层层级结构（登录/注册加####子节，讲义改为先按内容/按钮拆分再按子页细分）
c3181e3  feat: 新增 AuthRepository（登录/注册/登出），同步 UserRepository 引用，补登录/注册页面空壳
2e11a7b  feat: 实现全部 UI 页面和组件
962b2b8  fix: 编译错误修复（Icons.badge_outline → Icons.person, 语法 ?.[0] → 安全的索引访问）
db3bdea  fix: 按画布修正全部UI差异
9b9fafa  fix: 首页样式同步到 profile 的 Card 风格，问候语用同步数据消除闪烁
9cd14c7  fix: 解题模式已完成步骤不再折叠，改用 Set 记录已展开步骤
1530717  fix: 首页问候语显示 Closure 的 bug（ 缺括号）
dddca57  feat: 丰富全部 repositories mock 数据
d320f5a  更新SDK
11cfed7  新增 UI 原型 HTML 文件，覆盖全部 14 个页面
3c8cece  第1轮手工修改UI
4b4b446  整修：批语落实 + 新增页面精修 + 改版页面样式修复
0b6a356  第2轮手工修改UI
14a9603  第2轮整修：批语落实+导航规整+新增答案速览页
7cbe6c7  解题模式修复+个人中心加退出登录
01c81fb  解题模式交互重写：箭头展开反馈触发下一步
fd1358f  删除flutter_app和Django_service，等待docs编写完成再重建。
6c5bc55  修复解题模式交互：反馈只显示下一步卡片，不展开内容
9135853  恭喜完成追加在步骤下方+缩小+去掉'得分评估已记录'+下一题加注释
b39f665  更新UI相关文件和文件夹名称；修改solve.html按钮
c0afa17  三套标记体系：data-db(只读)/data-db-bind(双向)/data-db-action(写入)
2bda54a  新增Database文件夹
7d0e8bd  删除数据库操作汇总
e43a664  统一更新 data-db 标记为 Repository 命名规范（17文件 150映射）
56b9f70  新增项目架构与技术规范文档
a876f7f  更新文件夹结构，新增spec文件夹。
56f49b4  新增 Repository 层规格说明（8个文件）
9af58d5  精简架构文档：删目录列表+Repo对照表，更新工作流指向dart规格文件
87a426f  删除UI层_操作清单。
25202d2  新增ToDo文档。
fb327be  docs: 新增本地缓存与同步方案到架构文档
2f94c4d  docs: 简化本地数据方案 — 题库改为预置 + 版本号检查
9163cdf  feat: 添加同步引擎设计稿
5afe072  docs: 重写 ToDo.md，汇总待办事项
5e077ad  feat: add MdLatexBody component for Markdown + LaTeX rendering
9267a85  UI设计重构: 底栏改为作业/推荐/组卷/我的
a5ab7f9  更新gitgnore，忽略todo.md
14ef841  忽略todo.md时斜杠写错了，现在改正。
2b2a77b  停止跟踪 docs/ToDo.md（改由 .gitignore 管理）
40fd1e5  更新数据库结构
e2eec97  恢复并升级积分系统: 等级+三种积分+流水
740bbad  等级详情页: 去掉文字标记, 等级说明移至标题下方小字
fda0b48  修正积分数值: 累计22.0→Lv.5, 三者一致
3c4c6f2  讲义入口: 从我的移至作业页面顶部
c2db400  讲义返回路由: profile改为homework
8e0a49b  成就体系+学习统计+调试页
0867f60  feat: 新增退出页面评价弹窗功能
2340f11  feat: 组卷功能升级 - 智能组卷 + 自主选题
16388d4  feat: 组卷分享 + 点赞收藏 + 页面重组
479f66d  refactor: 所有返回按钮改为 history.back()
80a93db  feat: 学习偏好系统 + 推荐双模式
9175ba1  chore: debug页新增更新日志弹窗
0be0ca8  fix: UI名称统一与排序优化
6f4dae1  docs: 重写UI说明，全面覆盖28个页面
6ca2174  feat: 添加设计图总览导航页 index.html
519bfc5  chore: 生成单文件设计图总览（28页嵌入）
72c5740  fix: 单文件设计图总览修复路由跳转
9d9f4dd  统计页面：动态数据生成、布局调整、条形图热力分色
7e02871  统计页 data-db 标注 + styles.css 高亮优化
257938c  feat(ui): 难度/计算量滑条增加分段标签+箭头题型描述
67ccead  feat(ui): 作业tab改为首页，新建作业列表页，底部导航统一更新
087f78a  fix: 首页页头标题资源→首页
c424787  积分系统升级：4种积分+连续登录+每日任务+评价奖励+Toast通知
086e2b0  feat(ui): 我的页面拆分信息卡+分类重组，新增个人信息编辑页
867ea0d  UI: 统一用户界面显示昵称，真实姓名仅限管理员使用 - profile.html: 头像旁名字改为昵称 - profile_edit.html: 字段重排，昵称在前，真实姓名只读灰显 - register.html: 真实姓名/手机号提示改为提交后不可修改 - user_repository.dart: UserInfo新增realName字段
dbfed4d  UI: 新增关于/同步队列页面，系统栏入口，检查更新弹窗
0121afc  fix: profile.html底栏首页链接指向homework_list.html（原指向不存在的homework.html）
61f97bf  chore: 更新日志替换为增量版本（仅展示与上一版的差异）
18f44da  fix: profile.html底栏首页链接改为index.html（原误改为homework_list.html）
7777894  docs: 生成UI设计图v3（32页，新增关于/同步队列/个人信息编辑等页面）
ded3163  重构 Repository 层：13 个领域文件，简单/复杂拆分，私有算法类注解
aa10a31  更新 Repository 层规范：13 个文件、简单/复杂分离、跨页面数据组织规则
770f97c  合并UI说明入架构与技术规范，补充解题防刷/Flutter代码结构/SharedPreferences/难度映射等规范
35646c4  修正评分文案(10星/5级表情)，新增LaTeX渲染位点标注/路由方案/骨架屏规范/网络失败处理规则
7e2f941  评分规范：补充优雅度10星标注；conceptTags用Chip+Wrap渲染
249c1f1  weakConcept→recommendReason：推荐页字段名与UI标签统一更新
ec210d1  讲义：新增REVEAL逐段展开机制，LectureContent.blocks替代body+formulas
00f1ebf  图片存储方案：抽离 images 字段、ImageResolver stub、solve.html 配图区占位、头像本地优先
eb251e5  solve.html: 三题型分支 + 小问 tabs + 解法切换
f319715  feat: 新增本地数据库结构设计文档（drift schema）
7b6d3a9  docs: 合并数据库结构文档，删除user_preference，新增lecture_progress/题目状态推算
1cd3c87  docs: 合并数据库结构文档（删除user_preference/lecture_progress，精简为单一统一文档）
8e1dad5  fix: 对齐Repository与数据库设计(删studyStatus/congratsText, 加level_config/question_knowledge_card, 定义积分映射)
d7857b5  feat(lecture): 讲义数据结构改为方案B——客户端镜像存储raw markdown，渲染时解析分隔符
8c3c256  fix(solve): 补全填空题输入+判断，新增调试工具栏，修复计时器/箭头冗余/下一题刷新问题
35db49e  fix(solve): 填空题按钮主动查看，选择填空冷却10s
0c46690  feat(solve): 新增复访重建机制 + PreviousSolveState 数据类
1d56295  refactor(solve): 拆分解题模式原型，状态机/交互/工具三文件分离
aa68e7c  fix(solve): 修复复访模式三种题型的重建与冷却问题
225629c  Docs: 移除旧版过渡相关表述，改为新版纯 API + Admin 定位
ce23c7c  解题模式: 完成状态持久保留 + 解答题每步5s冷却 + 灰色/蓝色按钮
de6ef9e  解题模式: 修复复访倒计时残留 + CSS独立文件
f6ff7e1  解题模式: 题型页拆分 + 评分独立 + 完成横幅
27e28ce  解题模式: 外部路由更新 + 评分页跳转 + 题型引用迁移
6e4537e  架构文档: 解题页拆分 + 评分独立 + Widget复用规范
3c5abdc  解题模式: 选择题提交后绿色正确/红色错误 + CDATA修复 + 文档日期删除
4b55d81  拆分架构与技术规范.md为4份独立文档
c0ac53b  新增更新机制设计（后台下载 .db 整体替换），讲义独立 DB，统一版本检查 API
cdaee6b  更新机制 UI 原型 + 修正窗口规则 + 补充讲义版本显示
a8da6da  add: 教师端功能边界文档 — 角色定位/职责边界/页面清单/API设计/Admin职责划分
bb1e007  add: 认证方案设计 — JWT/角色校验/app_type参数/注册跳转/SharedPreferences 存储; 更新教师端文档第五章; 完善 auth_repository.dart spec
aff81d2  docs: 新增服务端架构设计文档 — App划分/模型映射/认证/数据库选型/settings清单
c207eac  docs: 新增API设计文档 — 通用规范/认证/同步/用户/教师共20端点 + 本地功能确认清单
b5f6ae9  docs: API设计文档统一加 /api/v1/ 前缀，重写版本控制章节陈述理由
4262a37  docs: 服务端架构/数据库/构建脚本三文档同步更新 — 加system.DbVersion/审计策略/构建脚本方案
725309b  docs: 服务端架构/构建脚本更新+着陆页+汇集发布版UI
2fbf9ce  design: 着陆页精简 — 去掉教师端入口/更新日志/联系管理员，统一用微信联系方式
1fbe274  design: 着陆页三平台下载按钮(Android/iOS/Windows) + 链接预留
603c751  docs: 新增系统架构图（7层分层设计 + 横切模块）
e22938f  docs: 更新架构与技术规范.md 第一节——7层架构替换旧ASCII图
4c037c8  docs: 页面设计说明——图表卡片节与实际原型对齐，移除具体图表类型待定标注
7ffef2b  docs: 新增数据访问层设计草案（DAO+ApiClient+Prefs+测试性设计）
22140a5  docs: 数据访问层设计——从静态工厂改为构造注入，移除setInstance方案
0a7bf27  docs: 数据访问层设计定稿，移除草案后缀
9454ef6  docs: 5个复杂算法注释更新——SQL改为DAO调用，删除独立核实文档
ad02ac1  docs: 推荐和组卷算法标记为极简v1方案，PDF标注架构决策未定
d220b84  docs: 同步队列重试策略合并入本地数据方案.md §1.8，删除独立文档
9f8310b  PDF生成设计定稿: spec/pdf/ + exam_repository尾部注释更新
8271cf4  修正分页规则: 选择/填空连续编排, 解答题每题独立起页
8d968f8  refactor: 解题页面重构——拆分解答题为流程图+步骤详情页，支持存档机制
6837aef  feat: 解题地图增加存档切换——下拉菜单选择第几次作答，支持回顾/重做/新存档
3970bde  feat: 选择题/填空题增加存档切换（回顾/重做/新存档），三题型存档交互统一
98eecb2  fix: solve-step.html 冷却按钮放入白底卡片内，消除点击前后的视觉跳跃
4f72f03  feat: 解题地图新增首次视图——全新存档显示欢迎/开始页面，防剧透
caebdd0  feat: 入口页路由参数化+题型分流，选填题取消欢迎视图，Repository补充存档模型
c3ca504  PDF方案重构: 服务端HTML→浏览器打印, Flutter仅留入口+引导弹窗
7cb5d4d  更新exam_repository注释: 标注_ExamPdfService已废弃, 指向新方案
5e239a0  同步更新关联文档: 移除_ExamPdfService引用, 更新ToDo/图片说明/架构图/数据类注释
eb9bb96  清理: 删除pdf_exam_input.dart (服务端方案不再需要Dart数据类)
5c80a7e  feat: 数据库适配存档机制——submission_detail加attempt_number+status，ProgressRepository增Attempt模型和存档接口
91dbd45  服务端文档添加PDF相关配置 + spec/pdf移入test_paper.html和配图
fa484ce  spec: 更新推荐算法引擎设计（冷启动/路线A/路线B/合并排序）
f087008  spec: 更新智能组卷算法设计（贪心+3轮交换优化/池子不足异常）
c49e938  spec+UI: 组卷 confirm() 加 allowShortfall 参数 + 池子不足弹窗UI + paper_auto 批语注释
1ca18b8  设计稿重组：扁平 docs+spec 合并为按领域分组结构
98cb7d5  补充：清理旧路径残留的 git 跟踪记录
1bbfd5e  card_feedback: 第二个 status 改名为 mastery_status（生命周期 vs 掌握程度两个语义）
3fdb026  修复：数据库结构设计.md 编码问题（UTF-16→UTF-8）
0260003  修复：solve-pages 7 个文件编码 UTF-16→UTF-8
a0a29c6  测试策略: 新增分层测试方案文档（7层：算法/DAO/Repository/Widget/E2E/服务端契约/构建更新），覆盖全部复杂算法类、API契约、E2E流程
8773eb6  测试策略: 移到 docs/ 根目录（跨 Flutter+Django+构建脚本，不属于服务端独占）
f450e38  PDF 功能：补齐设计阶段 5 项缺口
d69c463  fixup: 修正 PDF 设计的两处错误
aa577aa  PDF 功能：记录三点设计决策
75bbbe2  PDF 功能：双源支持 + 共享 PdfHelper + 全页面入口
23922a0  同步引擎测试: 新增专门章节（SyncPusher/SyncManager/server_id回填/推送粒度/边界异常），从8层扩为9层
d040cbe  Helper 体系：集中化索引 + 补齐 3 个 Dart 原型
26345f4  Helper 收尾：存档维度 + 私有化 + 清理 stale 引用
a4d2171  fixup: stage lecture_parser.dart deletion
cdb5b0c  PDF: test_paper.html 定稿（删除验证清单）, 设计方案页码规范同步修正
3442b5c  fix: 恢复PDF配图为有效WebP（重构时UTF-16编码损坏）
105f49d  PDF: test_paper.html 高仿LaTeX排版精修（行距/缩进/两端对齐/大题标题去线/页码/边距等19处）
dc53c93  PDF: 补充字体方案技术文档（Noto Serif CJK SC子集+Latin Modern自托管）
1c645d5  PDF: 解答题移除冗余writing-area（独占分页天然留白）, flex布局基线对齐修复
807d736  PDF: 移除解答题段落缩进, 大题标题page-break-after+break-after防孤行
83da93e  PDF: 填空题强制另起一页避免标题孤行（浏览器page-break-after:avoid不可靠）
740ab42  PDF: 新增3版布局对比稿（个人信息与章鱼智学标识位置方案）
fdaffb4  chore: 清理PDF变体生成用临时脚本
bbec002  PDF: 定稿V2方案（@bottom-left章鱼智学+@bottom-right昵称学号）, 清理变体文件
c2a94f2  PDF: 补充个人信息数据流到设计文档（视图查询+模板注入+排版规范+决策记录+TODO）
dbd288b  设计修复：sub_question/assignment_question 移除 attempt_number 残留；card_feedback 移除冗余字段；新增落地计划文档
6caa114  更新落地计划：线性化工作流、每步测试、题库迁移归入Phase1、用户迁移放到上线前Phase6
a5b10fd  补充基础设施：CI/CD、Sentry、Staging、API文档、DB备份，修正迁移映射错误，新增启动检查清单
39a573b  新增教师UAT验收阶段(Phase3.5)，含三次介入(解题初验/全功能UAT/上线前确认)
5115540  工作流原则新增「设计纪律」：按文档编码，不清楚先问，不擅自决策
f800633  chore: 清理PDF设计阶段的临时脚本
d9aacba  Phase 0 细化方案：新建落地实施/文件夹，Phase 0 改为简洁版+链接指向
1860b8f  忽略微信名片jpg图片
12905cc  微信名片文件改名
eb6faa6  着陆页：占位div替换为真实微信二维码图片
eb06ebe  Phase 0.2: Django 脚手架（5 Apps / settings / urls / flake8 zero）
0fa9587  Phase 0.3: Flutter 脚手架（flutter_app/ + Riverpod + analyze/test zero）
333f440  Phase 0.4: 着陆页（从 docs/07-工作流/landing 复制到根目录 + 补 privacy/terms）
9cee0db  Phase 0.5: Gitee Go CI - xin ban .workflow/ ge shi, bing xing Flutter+Django jian cha
661f52f  fix: displayName gai wei ASCII, qu diao zhong wen
7ef1a86  fix: jobs gai wei tasks, qu diao git-clone step
912ec47  fix: qu diao stages, zhi jie yong jobs
b10b5ed  fix: stages xia zhi jie yong steps, bu yong jobs/tasks
e171463  test: shell step yong run: qu dai inputs:
b80e3fb  fix: inputs.command + workDir zheng que ge shi
f6c9d36  fix: shell -> shell@agent, flake8 workDir server
ca44fe4  Phase 0.5: GitHub Actions CI（并行 Flutter+Django 检查），放弃 Gitee Go
2887ddf  docs: Phase 0 wan cheng zhuang tai geng xin, CI gai wei GitHub Actions
388ecea  教师端技术方案决策：学生App+轻量Web混合方案
af5190a  教师端：讲义阅读权限 + 编辑流程明确
6a2501a  教师端：细化Web端实现步骤，与Phase 2/3并行
d23837f  fix: CI pin ubuntu-22.04 (avoid Node.js 20 compat issues) + add missing .flake8 config
2447490  fix: use pip3/python3 explicitly, add debug step to diagnose CI runner env
ac81d3a  fix: Flutter use Docker container (ghcr.io/cirruslabs/flutter) to bypass subosito Node.js compat issue
d6af888  fix: manual Flutter install from GitHub repo, drop Docker/subosito dependency
3a4af8e  fix: download Flutter SDK tarball from storage.googleapis.com instead of git clone
61f2f1c  fix: use C:\Users\Annouimo instead of /opt (permissions) + verbose install log + flutter --version check
e0b4a5a  fix: add flutter pub get before dart analyze (missing package resolution)
0a48c27  fix: switch back to subosito/flutter-action with cache + flutter pub get
9280f26  docs: CI 文档更新——Gitee Go→GitHub Actions，反映流水线全绿状态
fd1f5d8  docs: Phase 0 检查清单全部打勾 + Sentry DSN 配置
d59f79e  docs: Phase 1 服务端全量细化方案（覆盖 1.1~1.8，每步测）
b5f912b  docs: 标注CI更新时机（🔧CI标记），Phase 1.3 和 2.1 各一次
8ed9ea5  feat(docs): 教师端 HTML 原型 — 9 页完整设计稿
507e026  Phase 1.1: 5 App models.py + admin.py + 初始迁移
dcae19a  docs: Phase 1.2 题库数据迁移细化方案（全量审核设计）
913fb62  Phase 1.2: 题库数据迁移完成（6步+数据清洗+试卷排序ID）
1475bfa  chore: 备份和审核文件移至 docs/_archive/，加入 .gitignore
822590a  chore: 迁移脚本移入归档，.gitignore 增加 db.sqlite3*
dd20ab8  fix: KnowledgeCard 补充 category 字段（流程/定理），回填 107 条数据
585e9ed  feat: 配图迁移到目录结构 + 去水印 + 替换6张问题图
cf741fd  feat: 学号系统改为模板+LCG自动生成
1594e85  docs: 新增学号生成算法文档；修正迁移计划说明
f006c1b  feat: 业务参数抽入 SystemConfig，新增 config_reader
c1897b4  fix(docs): 教师端原型修正 + API 文档同步
2f0b0c8  Phase 1.3: JWT 认证 API + pytest 测试 + CI 更新
6324bfd  docs: Phase 1.3 标记为已完成（JWT 认证 API）
b4106ae  fix(docs): 教师端原型细节调整
d8e0deb  fix: CI flake8 问题修复 — F401/E125/W391
93484ea  Phase 1.4: 同步 API（VersionCheck + SyncPush）+ 28 测试
4c1e294  Phase 1.5: 用户 API + 讲义 API + 12 测试
b4698e4  Phase 1.6: 构建脚本 — assets.db / lectures.db 构建工具
49225d5  test: Phase 1.6 构建脚本测试 (26 场景)
0b38ecc  docs: 验收检查清单 — Owner 六维验收体系（设计合规/数据正确/测试覆盖/异常处理/用户体验/安全部署），覆盖 Phase 0-6 及教师端
e2708b3  Phase 1.7: PDF 视图 — 签名 Token + 试卷 HTML 渲染
1b1c02d  Phase 1.8: Admin 系统工具页面 — 构建/邀请码/批量导入
682acbe  fix: admin tools 路由顺序 — /admin/system/tools/ 必须在 admin.site.urls 之前
31d8f71  docs: Phase 1.5 Staging 部署细化方案（含 nginx 路由分发+维护页面兜底）
c9b965e  fix: Phase 1 设计文档差异修复 — DbVersion/PaperCollect/audit字段
e197707  docs: Phase 2 Flutter 数据层细化方案（2.1-2.5，每步测，~189 用例）
b411058  fix: CSRF_TRUSTED_ORIGINS + SECURE_PROXY_SSL_HEADER for Cloudflare Tunnel
8b20f58  feat: auditlog 审计日志注册 + 7 项验证测试
fe80e75  fix: PDF 签名 O(1) 重构 + 选项渲染修复 + 测试补充 + Admin 注册补齐
0b94621  fix: CI flake8 — E402 noqa + 移除未用 import pytest
5ed85c1  Phase 2.1: 3 个 Drift Database + 11 DAO（内存 DB 可编译，0 error）
3962950  test: Phase 2.1 DAO 测试（88 用例，全部 memory DB）
6ba584b  fix: lecture_dao ORDER BY index 加引号（SQLite 保留字）
a0aac85  fix: CI dart analyze — 清除 28 个 warning（unnecessary ! / 无用 import / 死代码）
8dd7066  Phase 2.2: DatabaseProvider + ApiClient（3 拦截器）+ 12 测试
ded6dda  fix: build_schemas.py knowledge_card 缺 category 列
457ca4f  test: 新增 knowledge_card category 列校验 + chapter 列名修正
2ebde4d  test: CI 守卫 — 构建 Schema vs Django 模型一致性测试（方案 A）
11a8749  Phase 2.3: AppPrefs + ConnectivityMonitor + 16 测试
ee17bf1  fix: flake8 E127 缩进 — CI 守卫测试格式化
2058ba5  fix: 审核问题修复 — DatabaseProvider 测试 + Auth/RefreshInterceptor 测试
0b35d4f  fix: AppPrefs 补全 ratingCooldown 方法+测试
15f1d1d  refactor: database_provider_test 从 raw SQL 改为 Drift typed API
baba446  refactor: DAO 层从 raw SQL 全面改为 Drift typed API
bb02e67  fix: 3 个 API 层违规问题
49e7e7e  fix: CI dart analyze warning 60 to 0
8448821  fix: 恢复重写时丢失的中文注释和段落分隔线
8a1c8bf  fix: 错误码规范化 + 等级计算改用 LevelConfig 表
9a1c9e0  fix: 错误码进一步规范化 — 注册 40101 / 业务校验 40201
ccc2aca  docs: 更新落地计划状态标记 — Phase 1/1.5 标记完成，Phase 2 标记进行中，逐项对照验证
46a700c  Phase 2.4: 13 Repository 实现 — 构造注入+实例方法，含 5 个尾部算法类（v1），修复 sync_api URL 模板
93d417a  feat: 补齐 question_status_helper 和 pdf_helper — 题目状态推算（全局/存档双视角）和 PDF 下载流程
418d744  test: helper 测试 — question_status_helper 11 条（全局/存档/批量全场景）
e3f3bf0  test: Repository 集成测试 — 13 个 Repository 共 57 条用例（memory DB + mock adapter），补齐 Phase 2.4 测试缺口
156d775  fix: 补齐尾部算法类 + 单元测试 — ExamFilterEngine/StatisticsAggregator/PointsCalculator 实现+测试共10条，类名改为public以支持测试
33f9634  fix: 尾部算法类恢复为私有（_ 前缀），测试改走 Repository 公有方法
1cd8be2  chore: add .hermes.md with temp-file discipline rules
a7e76c6  Phase 2.5: 同步引擎+更新机制 — SyncPusher/SyncManager/UpdateManager + 16 测试，SyncQueueDao 补 cleanup+markPermanentFailures
14f8f9c  docs: Phase 2.5 标记完成
fae96d0  chore: gitignore build_old* 残留目录
ad73fd5  Revert "chore: gitignore build_old* 残留目录"
145974c  fix: 审计修复 — 崩溃Bug/缺失引擎/缺字段/文档滞后
ab2fb76  docs: 落地实施文档重组 — Phase-0/1/2 拆分+模板规范化+验收清单补全
900e5e9  docs: 修复合集 — 模板文档+2.5拆分+格式统一+清单引用
4897905  docs: 验收门槛改为零容忍(去掉有条件放行)+修正已完成Phase的状态标记
246982f  docs: 补执行记录+统一子步骤节标题(Phase-1/2.x)
bf30dff  fix: 2.5 审计修复 — UpdateManager/启动链/serverIds逐条处理/SyncQueue serverId列/测试补全
499231d  docs: 修复6个遗留格式问题
2708bb7  docs: Phase 3 Flutter UI 细化执行方案 — 8 子步骤（3a~3h）合计 ~97 测试用例
95f8d60  fix: 审计后半段 — ExamGenerator 3轮交换优化/RecommendEngine完整/Exam/User stubs补齐
90e7259  docs: Phase 3 细化方案 — 删除'不启动总测试数验证'错误备注
94d67ad  fix: 第3轮审计修复 — 掌握度引擎/交换优化注释/onAppStart版本检查/stub方法降级
ee5374c  docs: Phase 3.5 教师 UAT 验收方案 — 9 模块验收脚本 + S0-S4 问题分级 + 签收流程
d5417a4  docs: Phase 4 辅助系统细化执行方案 — 成就/积分/评价弹层/同步队列/首次引导 + ~50 测试
0302bcd  fix: 第4轮 — 时间衰减/小样本收缩/卡片卡住率/getFavorites实现
41c7715  fix: 第5轮 — getLevels/getDailyRecords/今天积分/questionBankVersion 全实现
5ade143  docs: Phase 5 集成测试细化方案 — L6 API契约全覆盖 + L7 E2E(本地跑不跑CI) + L8构建验证 + ~16 新增测试
3c66246  docs: Phase 6 用户数据迁移+上线细化方案 — migrate_users脚本/教师终签/正式部署/着陆页/Sentry观测 + 操作清单
4102132  Phase 3a: MainShell + 登录/注册 + 首页 + 主题/路由骨架 + 25 测试
7e27eac  docs: Phase T 教师 Web 端细化方案 — 7子步骤(T.1-T.7) 纯静态HTML/CSS/JS + 12条手动验收路径
6b2d29f  Phase 3b: 解题模式 — CoolingTimer/FeedbackButtons/SolveFlowWidget/StepCardWidget + 解题5页 + 路由 + 17测试
59a5a7f  fix: Phase 3a 审计修复 — RegisterPage构造注入/核心路径测试补全/widget_test标题/api_client花括号
7f3223f  fix: Phase 0 — SQLite IMMEDIATE/真实SECRET_KEY/12个W002/CI冗余安装
4af8815  fix: Phase 3b 审计修复 — MdLatexBody/数据绑定/构造注入/isCompleted/反馈入sync/下一步导航/测试+6
2baf87c  fix: CI — 移除 register_page_test.dart 未用import/参数（2 warning→0）
f8ef08c  chore: 清 dart analyze 14 条 info — withOpacity→withValues/__→_/+→\$ 插值
b49997e  fix: 问题7 — SolveRatePage 算法评分从 DB 读取而非硬编码 + 恢复已有用户评分
02eb971  fix: Phase 1 — points_summary/level_percentile结构对齐 + PDF本地化
c9ccc18  fix: 问题8+9 — submitStepFeedback/submitRating 入 sync 队列 + RatingRepository 读算法分 + QuestionDao 构造注入
4b4f429  docs: 更新migration_audit路径引用为docs/_archive/migration_audit
f8f4857  fix: Phase 1 — P1-6 phone保存/P1-8删batch_import/P1-10 chapter_list修正+文档同步
7e8f2f5  fix: P1-6 update_fields补phone + P1-9 PDF URL示例对齐实际代码
2c922f7  fix: P2-1 userCache json解析 + P2-5 RefreshInterceptor复用Dio实例
3540775  Phase 3c: 讲义三级下钻 — courses/chapters/content + 翻页/逐段展开 + 14测试
fc9e61a  docs: P2-4 数据访问层设计.md 单例描述修正(唯一→基础设施)
f46e0b2  fix: F401未用Q导入/PDF密钥三重复注释/RatingRepository测试补依赖
1bd5ea2  fix: Phase 3c 审计修复 — 5 个问题全部修复
f2235ce  Phase 3d: 作业列表+详情 — list/detail + 课程名查询 + 8 测试
a7e3b01  fix: 注册phone/refresh包裹/chapter_content字段对齐+测试
8ba109f  fix: Phase 3d 审计修复 — 4 个问题全部修复
e6af037  fix: ConnectivityMonitor种子值+设计文档同步(BehaviorSubject→StreamController)
5c5f59a  Phase 3e: 组卷系统 — 8 页面 + 3 共享 Widget + 7 测试
3ae6a32  docs: Phase-T 补 TS.1 服务端教师 API 实现方案（9 端点 + ~20 测试）
bd7b97e  TS.1: 服务端教师 API — 9 端点 + 22 测试 + flake8零问题
326c738  fix: Phase 3e 审计修复 — 5 个问题全部修复
f5dbd5f  fix(TS.1): 5项审计修复 — avgAccuracy/description路由/setattr崩溃/SwaggerW002/测试增强
3b0d34f  Phase 3f: 推荐页（双模式）+ 3 测试
d65c693  Phase T.1: 教师 Web 框架 + 登录页 — 4 文件
382df70  fix: CI 报错 — dart analyze warning + flake8 E402
a77eeba  Phase T.2: 作业列表(主页) + 发布作业 — 4文件
77b7e24  fix: 推荐页审计修复 — 3 个问题
ddabdd0  fix(T.2): 3项审计修复 — class_list/id/聚合统计/死代码
34106ed  Phase 3g: 学习统计页 — 4 图表 Widget + 页面 + 路由 + 11 测试
b57ee93  Phase T.3: 作业详情页 — detail.html + student-row 样式
32a3d3d  Phase 3h: 个人中心 — 7 页面 + 路由 + 11 测试
a8c2958  fix: duration 字段 — 从 SubmissionDetail 时间差计算真实耗时
4868d28  Phase T.4: 班级概览 + 学生列表 — 2 页面
f59a79b  fix: 成就页硬编码 + 编辑资料缺手机号 修复
0078ac6  fix: 班级概览补 totalQuestions 统计卡片
7269b63  Phase T.5: 学生详情页 — student.html
d3a84bc  docs: Phase 3.5 → Phase 5 教师UAT验收方案 重构 — 改名/补充Phase4验收项(成就/积分/评价弹层/同步队列/引导)/标注与Phase5并行关系
3729b58  Phase 4.1: 成就引擎 PAPER_COUNT 从 stub 改为 ExamDao 真实查询
fd959f2  docs: 00-落地计划同步修改 — 教师UAT验收从Phase 3.5移至Phase 4后+与Phase 5并行/验收范围新增Phase4产出
0305a25  fix(T.5): 3项修复 — school/registeredAt/SVG折线图/weakTags正确率
eb72136  Phase T.6: 编辑资料 + 关于页
a3bd563  Phase 4.2: 积分引擎 _PointsCalculator 单元测试覆盖
1fc8200  fix: about.html 隐私/协议链接改为根绝对路径
43746e0  Phase 4.3: 退出页面评价弹层
9916a88  fix(4.3): 补齐测试覆盖至 10/10 + @visibleForTesting 公开弹窗类
9cea045  fix(ci): dart analyze 零问题 — 40 个 issue 全部修复
b1b2a8f  Phase 4.4: 同步队列状态页面
99fdeaa  fix: about.html 硬编码→API动态加载
952f165  Phase 4.5: 首次引导流程
06b2f36  docs: 同步所有落地文档状态为真实完成状态
d360858  fix(4.5): 欢迎Dialog + PreferenceFilter补全5字段 + 积分实时读取
c8a0bce  feat: system_config 表 + ExitRatingConfig 从 DB 读取 + submitExitRating try-catch
f42172b  docs: system_config 表定义 + 退出评价/冷却规则配置来源更新
30ed66b  Phase 5 L6: 服务端 API 契约 — 新增 7 条测试
5189505  Phase 5 L7: E2E 测试 — 4 条路径 + 驱动入口 + 运行脚本
21f5693  Phase 5 L8: 构建验证 — 幂等性测试
66a17d5  fix: 3 项审计问题修复
795a034  docs: Phase 5 状态 待开始→已完成 + 测试数 89→122
80b2b09  landing: 着陆页样式与交互改进
35c1428  docs: 用户数据拉取机制实施方案
d9854eb  feat: 用户数据全量拉取机制
e100b6d  fix: pull 端点生成前自动清理超5分钟的临时文件
24d316e  docs: 补齐用户数据拉取机制相关设计文档
33545ae  feat: backup_db.sh — 每日数据库备份脚本（方案 B）
9e3b849  docs: 备份方案（B + C），详见 docs/备份方案.md
359e5b1  feat: dump_data.py + load_data.py + dump_and_push.sh（方案 C 备份脚本）
6ff8888  fix: dump_and_push.sh python→python3
361f795  style: flake8 — 修复 E231 空格问题
56c886d  feat: 同步进度展示 — 登录/关于页统一进度弹窗
ce7392a  docs: 同步进度展示相关文档补齐
c2e62bb  fix: 题库/讲义版本检查结果接上更新 UI 流程
b07376f  docs: 审查流程手册 — 7 类审计分类、文档映射、力度要求、陷阱清单
6ec2a3f  docs: 审查流程手册 v3.0 — 改为文件夹全覆盖矩阵，移除 Phase 引用
4b91875  fix: add bundled assets.db and lectures.db for Windows startup
98d9cf0  docs: 审查流程手册 — 新增pubspec.yaml资产声明验证（配置文件盲点陷阱#9）
12e4d35  cleanup: remove teacher profile.html (已废弃)
6a142a1  feat: add SystemToolsProxy admin entry for tools page
3ae1816  fix: VersionCheckView 返回绝对 download_url，修复 Flutter 下载更新崩溃
b189586  docs: 审查流程手册 — 新增跨层格式一致性probe（Type A+B），可检出download_url相对路径bug
c0a8efe  fix: 5项问题修复 — remind端点/course_id/message字段/积分分类/pull_user_db测试
7c8a6ef  docs: 审查流程手册 — R7强制HTML↔Flutter元素对比表, Stage4细化, Step0改阅读顺序, 陷阱#8重写
a4dfadc  fix: 5项Flutter问题修复 — LaTeX渲染/翻页/积分测试/catch静默/首页
4793015  fix: 全面对齐HTML原型 — 首页/导航/解题地图/作业详情/评分/统计/偏好/Toast/解析
8568b82  docs: 审查流程手册 — 新增assets/questions/覆盖矩阵+B8配图目录probe+Step0提取待完成标记+陷阱#11后续待完成
1e90d39  fix: P1/P2/P3 — flutter_markdown_plus迁移 + 设计文档对齐
6fcbb14  fix: index_page_test更新+PreferenceListPage数据绑定
9fe70ef  fix: index_page_test 异步修复+PreferenceListPage数据绑定
a44efd7  fix: SolveRatePage submit 测试 — 按钮文本匹配实际显示
36c8e75  feat: 配图管线全线打通 — AssetImage离线加载+98张配图同步
2141620  fix: 5项教师端修复 — Teacher name/准确率数值/连续签到/题型分布/PATCH title
157fdac  fix: 5项问题修复 — dump password/load_data/migrate/deploy/env/deadline字段
59d5f33  fix: deadline DateField适配(tests: 24/24 pass)
982421b  fix: 统一教师端API正确率/完成率字段格式为数值（问题8）
5af8dd4  fix: 10项设计合规修复 — 文档补齐/路由清理/测试覆盖/状态更新
fa578d7  feat(admin): 管理员使用说明页面（Django Admin 内）
7d3dd62  fix: 8项修复 — stats趋势/Pdf委托/推荐预设/存档重建/设计文档
51cce51  fix: 头像上传绝对URL + Flutter头像上传UI
17f8f33  fix(admin): 修复管理员说明页目录缩进和配置键值列宽
daee014  chore: 补提交 build_runner 生成的 platform registrant 文件
ddb0efc  feat: auto-audit engine + manual + skill — R0文档清单先行自动化审计
3ccfae4  docs+engine: 手册加入A-G速查+命令汇总, 引擎支持--type按类别过滤
1304b91  engine: 清理未用函数+import, 修复lint警告, 保留旧手册
b172e7e  docs: 移动旧手册到auto-audit, 新增审计命令速查(7种类型×2种skill)
68782c4  fix: CI失败项 — recommend_repository_test+flake8
fe0fa7e  chore: gitignore audit_report_latest.txt (运行时产物)
d2e83d1  engine: 模块2扩展 — HTML关键页面UI元素清单提取（R0输出），覆盖7页面80元素
cf5d741  fix: 审计报告修复 — 崩溃路径/stub/错误UI/TODO/页面缺失
f403932  docs: 流程步骤重编号0→6, 新增Step2关联推断(Synthesis)
466087b  fix: 补提交 — 冗余!移除 + 0005_adminhelpproxy migration
29b7651  fix: preference_edit_page — 未使用变量+花括号
7cd943e  fix: Type C Flutter UI 审计问题修复
054720e  engine+docs: 新增docs/06-教师端/html/路径检查, Step5模型约束, 手册4.6-4.7
9717252  fix: 7项问题修复 — 偏好编辑/退出登录/签到API/元信息区/作答次数选择器/Repository替换/dart analyze
ce6a82a  fix: Type E 部署审计 — 修复 accepted-deferred 注释位置
00f0c05  fix: 同步 preference_edit 测试用例 — placeholder→筛选条件卡 assertion
23abfcb  fix: 部署审计2项问题修复 — nginx /media/ + PDF_SECRET_KEY环境变量化
5e914b7  fix: 教师端审计设计文档同步 + 补充3项测试
94cff2a  fix: 7项服务端审计问题修复 — PageSatisfactionFeedback + 路由清理 + 文档同步
5416a87  fix: N项问题修复 — 清理死代码 + 同步设计文档状态
6075dab  fix: 3项UI对齐修复 — 推荐页pill切换/个人资料卡片可编辑/过时注释
7d450cf  docs: auto/手动skill合并为单一skill, 命令速查+手册同步更新
0aaa53f  fix: Type A 审计文档同步 — API设计.md 字段名 camelCase 对齐 + test_paper.html 本地资源 + PDF_SECRET_KEY 注释
139f486  fix: 删除 user_repository.appVersion() 死代码 stub
81e2822  fix: 删除 user_repository.appVersion() 死代码 stub
b47b4e8  fix: 6项静默错误吞除修复 — 添加 ErrorPlaceholder 错误状态
0924bdb  fix: Type E 部署审计 — 补CI pytest参数 + .env.example缺值
1e49cf8  fix: 教师端4项问题修复 — 分组详情/correctCount/streakDays/导航/文档同步
4d402e5  fix: 3项文档新鲜度问题修复 — 测试策略状态/备份实施清单/Phase4前提条件
0fef93f  fix: 5项问题修复 — token提供器/登录状态持久化/注册居中/偏好预设选择器
b99345d  Merge branch 'master' of https://gitee.com/annouimo/zhangyuzhixue-v2
2248336  fix: token过期自动跳转登录页 + 拦截器调试日志
6b9c382  fix: 签到按钮无限宽布局 + gaokao_year类型转换崩溃
bf0a10d  fix: checksum校验 — 客户端改用gz压缩后hash, 与服务端一致
dd83960  chore: 忽略 DevTools 自动生成的 devtools_options.yaml
00ef4e9  feat: 审计引擎新增H0-H3模块 — 初始化链(⑧)/API类型安全(⑨)/跨层算法(⑩) + 增强模块⑦ + 2.1手册
d2c288e  feat: 审计引擎新增模块⑪ — 捆绑DB内容完整性(H4), 查出assets.db/lectures.db全0行
43b1575  fix: Drift 表名对齐设计文档(单数) + seed 等级/成就数据 + pending_homework_count 持久化
2d62acb  fix: homework_list_page_test 添加 AppPrefs setUp 初始化
ba3bacb  fix: 服务端 checksum 改为对 .gz 计算（匹配客户端 hash 方式）
b10d69d  feat: 运行时审计系统 — audit_logger + 35页/12DAO/Prefs/Sync注入 + 引擎模块⑫(Runtime) + skill runtime-verification
610fb01  fix: 测试文件 _meta→meta 同步更新 + 验证 31 passed
e2fe499  fix: 子代理补充注入 — progress_dao审计日志风格优化 + system_config_dao移除审计(键值缓存无需)
fc9868c  fix: 26处审计日志注入修复 — AuditLogger.page→instance.page + 字段名对齐实际代码
be00f60  chore: 消除dart analyze warning — _presets非空因此去掉?.
313cd92  feat: 模块⑫增强 — 服务端预期vs审计日志自动核对 + 测试账号test_audit脚本
af7c847  fix: schemaVersion 3 + 旧 user.db 检测重建
a72a340  feat: 运行时错误捕获 — audit_logger.error/apiResponse + Dio拦截器 + 全局钩子 + 60+catch注入 + 引擎第7/8项断言
58e2f50  docs: 版本号体系区分 assets/lectures vs user.db 的 schema 变更策略
f6e3f84  docs: 新增runtime-verification手册 — 完整工作流/8项检查/日志格式/常见问题
596c9ca  docs: runtime-verification手册改为友好格式 + 速查表新增Type R
6437efb  style: seed_levels_achievements.py flake8 合规
5a0cbfa  fix: flutter run 的 cd 路径改为 flutter_app 子目录
f5d5238  feat: 模块⑫服务端核对支持远程SSH拉取DB — 同时输出[Local]和[Remote]比对
8d86290  docs: 更新手册 — 服务端核对说明改为Local+Remote双源
e0ee08e  fix: 3项运行时审计阻塞修复
f525cac  fix: ExamPickPage 移除width:double.infinity — 让CrossAxisAlignment.stretch自动拉伸
a77957c  fix: ExamPickPage — 移除搜索按钮SizedBox(width:double.infinity)
2f70568  fix: ExamPickPage — 重写 build 方法，完全移除 CustomScrollView+Sliver
3f824f7  debug: ExamPickPage — 添加LayoutBuilder日志输出body约束值
5aafb00  debug: 添加内层LayoutBuilder — 精确定位Column子组件中无限宽来源
8fd2d8d  debug: 底部Container用Text替代ElevatedButton — 验证是否按钮导致崩溃
c6a6e21  fix: ExamPickPage ElevatedButton加SizedBox(height:40)包裹
bedc317  chore: ExamPickPage — 清理调试LayoutBuilder，保留SizedBox(height:40)包裹
411d1fc  fix: ExamPickPage Row中去掉Expanded，改用spaceBetween
275d703  debug: 底部Row和ElevatedButton加LayoutBuilder精确定位
e7f8a3d  fix: ExamPickPage — 底部Container加height:56阻断无限高约束链
58ca4d7  fix: ExamPickPage 崩溃彻底修复 — SizedBox包裹ElevatedButton阻断无限宽
a1d856e  fix: 测试基础设施 — 全局FlutterError.onError钩子+桌面尺寸测试
9daefa6  feat: 新增测试质量检查(H7)和运行时模式分析(R12)
2c42828  fix: 3项运行时审计问题修复
4dcfb44  docs: 新增视觉审计手册(Type V) — 方案设计稿 v0.1.0
113f667  docs: 视觉审计手册 v0.2.0 — 分组/fail-fast/复杂交互/截图存档
efe6baf  docs: 视觉审计手册 v0.3.0 — flutter run启动+项目内截图目录+gitignore
1e37311  docs: 视觉审计手册 v0.3.0 — 增加Skill命令速查列表
0fdfcfc  docs(auto-audit): 更新Type V工作流—用户先手动启动、窗口硬编码390x844、缩短等待时间
e67184c  refactor: 分离自动走查/视觉分析，整合为R/RV双模式
fdfe764  fix: registry + GROUP_MAP 补齐全部 35 页导航路径
b77ae7b  chore: 删除审计命令速查.md, 命令移至各手册头部
205822a  refactor: visual-audit手册.md 合并入 runtime-verification手册.md
afb4f35  doc: 拆分Skill命令为R/RV两行，方便直接复制
193ef35  runtime-verification: 基于HTML设计图推算按钮坐标，重写walker click_text以坐标映射替代stub
54fc8c1  runtime-verification: DPI缩放检测+坐标缩放层，walker窗口自适应DPI
d1c56f4  fix: Tab3坐标修正(335→341) + 解题流程添加选答案+提交步骤 + 答题按钮坐标
f63087f  fix: 越界保护 — click_tab/click_text超出窗口时跳过，防止点到任务栏
dfa31a9  fix: 创建test_audit组卷测试数据(3套，2公开1私密)解决空态问题
7456dd0  fix: 截图目录加时间戳+清理旧截图(仅保留最近3次)
ad72a6a  fix: USER_DB_SCHEMA全部14个表名单数化(匹配Drift模型)，解决每次重启删用户数据的问题
52594a6  fix: 组卷详情页题目卡片加做题按钮(ExmQuestion加questionId+InkWell导航到解题页)
aad25fb  fix: 审计引擎补盲点 — 新增模块2C/2D检测HTML交互元素缺失(paper_quicklook 21vs9)
28afaa1  fix: Tab3坐标325 + 自主选题坐标修正(移除冗余偏移)
097887a  fix: 审计引擎全覆盖 — solve-pages 5页+input/TextField模式+报告LIKELY修复
146f720  fix: 引擎增强 — onclick/输入背离/条件死按钮三项新检查
936cd36  fix: Type C UI 全量对齐HTML原型 — 11项修复
51dc00c  docs: 补充 currentLevel() 方法到 UserRepository 设计文档
240a643  walker: 实时 OCR (内存) + 删除 coordinate_map + 返回按钮硬编码
f5697a8  find_window: 通过窗口类名 FLUTTER_RUNNER_WIN32_WINDOW 识别
33a7a41  walker: OCR 截图直接保存到审计目录 + 移除废弃的 numpy/mss
6ae4406  截图/点击坐标用 ClientToScreen 替代硬编码 +8/+30
dba5e9c  walker: OCR 复用最近一张 _full 截图，不再单独截 _ocr
2bfa921  click_tab 改用硬编码坐标（PaddleOCR 对灰色小字识别率低）
8ca2ea6  walker: CLI 交互式模式 + 手册/skill 更新
f72be20  docs: 新增基础功能排查清单（auto-audit）
7391262  fix: 切换 Tab 到推荐页时自动刷新数据
0e4c478  docs: 重写运行时审计手册（三步循环模式，替代旧版全量走查→R→Vision）
cbb31aa  docs: 运行时审计手册增加快速启动区（10个模块一键调用）
ee64990  chore: 清理 auto-audit 废弃脚本（nav_engine/vision_report/旧截图）
3b7169b  docs: 模块0 前置准备打勾 + 修正 build 命令
400815a  docs: 合并 fix-batch-workflow 到运行时审计手册（Phase 2 含核实，Phase 3 含方案与执行）
304cc89  fix: 签到成功后在本地 user_login_log 插入记录，下次启动 streak 正常显示
1355699  fix(auto-audit): 删除不存在的讲义知识标签项
536d8d5  fix(auto-audit): 根据HTML原型完整审计修正排查清单
eafb608  fix(lecture): 注入讲义分隔符并更新排查清单
a35aff8  fix: 4项修复 — 展开计数/公式溢出/清单清理/版本信息
877d7d1  fix(data): 补全测试数据三项缺口
3582b7d  docs: 排查清单模块0补充数据准备步骤，总计80项
37aa5b3  feat: 构建后自动清理旧版产物，保留最近2版
348d278  fix: 修正讲义第1章容斥公式溢出 — 行内→块级 + 文档说明
0a28649  revert: md_latex_body.dart 回退 ScrollView 改动 — 由数据修复替代
54b69a7  feat: ECS 查询脚本 ecs_query.py — 封装 SSH + Django shell，支持 health/check-user/count/sql/models/files
00aa83a  fix: ecs_query.py f-string 逃逸问题修复（sql + count），返回结构化 JSON
fed0057  docs: 更新 runtime-verification手册 v3.1 — winnav 增强(y_range/click_at/scroll修复) + ecs_query 脚本
7b17b09  fix: ecs_query.py 两个工具 bug 修复
704c841  docs: 按钮坐标表 button_positions.md + 手册引用更新
85398a5  docs: 翻页栏按钮校准坐标（◀ dx=57 dy=-66, ▶ 对称推算）
2ac51a2  fix: 2项解题模式问题修复 — 解析区LaTeX渲染+答题后进度刷新
834d3e8  fix: 讲义展开块视觉统一 + LaTeX行内公式折行/块级缩放
aaf50b2  feat: data_db_verify.py + verify命令 — 192条data-db路径全量映射
6d82552  chore: .gitignore verify_results + ecs_query.py --json logo suppression
85f9cdc  fix: 6项问题修复 - CrNode/nextId/文字重复/提交持久化/刷新/冷启动时序
b67badb  feat: ecs_query.py verify 写入缓存 + page 子命令, .verify_cache/ 列入 gitignore
02bb470  fix: data_db_verify.py 远程 worker 全量硬编码修复
937de6e  docs: 手册同步 skill v3.2 — 五步闭环 + verify/page + 状态检查点
ba83ac7  docs: 手册 winnav 工具表补全 winnav_type + winnav_close 描述
2e0f9fe  feat: 数据不匹配4方向排查框架（skill+手册同步）
9a4dc2f  fix: 选择/填空题解析回退到 solution_step.content + 知识标签弹层查真实内容
a2cc3e1  fix: 配图路径反斜杠归一化 + saveAttempt 首次提交创建 attempt
adafc60  fix: 4项组卷模块阻塞修复 — 试卷名称输入框+保存偏好+conceptTags+快对答案入口
6608223  feat: add snapshot_logs.py for archiving NDJSON + winnav logs
4e13ee8  docs: 重构审计文档体系 — 删旧runtime-verification手册，新增审计skill备查
fd60959  fix: 推荐引擎 N+1 查询优化 — 40,000+ 次查询降为 7 次
10c6d13  优化审计skill
1565da4  fix: 3项问题修复 -- 作业列表标题/学习偏好副标题/菜单数据摘要
e34343b  git忽略审计日志
19024ef  fix: 填空题页拆分 RevealWidget — 移除TextField/查看答案/元信息栏/文档同步
14c96f5  fix: B1 崩溃 — 组卷页保存偏好弹窗 _dependents.isEmpty（addPostFrameCallback 延迟 pop）
e0a42ac  refactor(solve): 填空题页改为揭示答案模式（SolveRevealWidget）
6a62aa9  fix: 审计 6 项问题修复 -- 发现页is_public过滤/ISO时间戳/待办作业API过滤+deadline
d36f514  docs: 新增 competitive-audit skill 到审计备查
a42b5d3  fix: 审计 profile 页 5 项问题修复 -- 同步后崩溃/自动刷新/last_login/文案
9346f42  fix: round2 audit 3项修复 -- 积分计算/题型分布/类型统计
a7b77a5  fix: visual audit round3 3项修复 -- 死按钮/版权/版本号
8fadb38  fix: R1-5 待办作业计数 — user_db拉取携带accessible_course_ids
e8cd18c  fix: mock syncAccessibleCourseIds in profile_page_test
531882b  fix: filter全面重构 - 消除3路复制+补齐HTML差异
de09f6d  chore: remove unused _selectedExamTypes/_selectedKnowledgeCards fields
8032f88  fix: preference_edit_page 改用FilterPanel + FilterPanel折叠toggle
c1ccf5b  fix: 保存/读取偏好 补充 examTypes 数据链
45b7295  fix: 筛选条件全维度接入DAO查询 -- 概念标签/知识卡片/考试类型/题型多选
16f9249  fix: 补齐偏好持久化 knowledgeCards/questionTypes 全链路
aebfe23  docs: 审计skill备查新增§五横切探查工具(cross-cut-investigation)，更新五者协作关系
460dd5c  fix: 添加 fontFamilyFallback 全局中文字体回退配置
9910471  fix: 积分系统6项修复 — 退出评价source统一/组卷扣分/服务端补充/文档同步
b8cec16  fix: 注册赠送10积分 + migration SOURCE_CHOICES补REVIEW_REWARD
da9ecfa  fix: 解题页面12项修复 — mode/attempt_id路由+存档管理+UI对齐HTML原型
e3001a1  fix: 补修pre-existing测试失败+知识卡片TODO清除
428e4a7  chore: 移除 index_page_test 未使用的 import
af2ec92  fix: 同步推送系统9项修复 — entity_type命名对齐/数据字段修复/connectivity检查/入队补全/测试修复
677a4ab  fix: PDF生成 6项问题修复 — API路径/引导弹窗/sig续期Timer/异常处理/URL斜杠/文档同步
1495e92  fix: 同步推送payload字段对齐 — rating字段名(→_score)+step_feedback补submission_detail_id
b5479d0  fix: 硬编码常量抽取 — baseUrl/组卷积分/导航路径/颜色值/debugPrint
1a1eb9a  fix: 筛选widget 7项问题修复 -- segment描述/Card容器/自动搜索/偏好名称/补齐维度/DAO计数/测试对齐
3aa7057  fix: 第①批Widget复用提取 -- PaperCard+ActionChip共享化+常量抽取
fef6bba  fix: 第②批逻辑合并 -- SolveRouteHelper+偏好弹窗+预览卡片
592348d  fix: 第③批信息级修复 -- AssignmentCard共享+PointSummaryCard+LoadingIndicator统一
bc584ad  删除实施文档，免得误导agent
818f449  fix: Flutter UI对齐HTML原型 — 16项修复
1a2733c  fix: 积分系统5项修复 -- transactionType大写/趋势过滤/旧名移除/SQL过滤/复用_PointsCalculator
850ce3b  fix: 同步系统6项修复 -- submissionDetail/cardFeedback入队+AuditLogger+connectivity重检+设计文档同步+pusher测试
8ca4836  fix: 4项筛选问题修复 -- 自主选题selectedIds锁定+筛选条件补齐+初始池统计+推荐预设维度补齐
3f3e1b5  fix: 同步系统三侧对齐修复 -- submission枚举改名+step_feedback/card_feedback detail_id置空+服务端排序+4xx区分+DAO加markPermanentFailure
e0679a8  fix: 6项推荐系统修复 -- mode/resume路由+全correct短路+解答题排序+SQL优化+UI对齐+测试对齐
8485dd9  fix: 6项偏好系统修复 -- 编辑传ID+race condition+Hero卡片+筛选校验+删除确认+emoji对齐
6b8bbd0  fix: 配图数据修复 — 清理stem中<img>标签+遍历配图文件重建images字段
bf82393  fix: 4项筛选UI修复 -- 池难度范围显示+Stepper可用数+HTML知识卡片区(2处)+设计文档FilterOptions补齐
56c8e36  fix: PDF 8项代码问题修复 -- N+1查询/类型校验/stem配图剥离/定时器泄漏/超时保护/key去重/context参数
ab5002d  fix: 3项推荐系统修复 -- welcome导航推荐页+真实做题状态+英文枚举+isCorrect=null跳过
666e1da  fix: submission payload加details[]数组+API设计文档字段名对齐
c042f90  fix: 积分系统2项修复 -- 评分积分创建+每日任务奖励
e24fb5e  fix: 解题页下一题后返回按钮丢失——context.go改为pushReplacement
9137e9c  revert: 移除PDF视图两处强行兼容代码 — stem <img>剥离/图片路径反斜杠归一化，数据库数据问题由专人修复
0365d6d  fix: 统计页7项问题修复 -- 热力图日历重构/streak做题数据源/Y轴固定/环形图中心/设计文档/测试Mock补齐
41fb73a  fix: 统计页'全部'模式返回空数据——rangeDays=0时不加时间筛选
6bf60bd  fix: 等级系统8项修复 -- 15级体系对齐HTML原型+服务端等级计算修正+首页等级进度文案+LevelRow扩展+徽章图标+积分查询合并+满级范围+离线缓存
bc0c123  fix: 成就系统升级 — 6类22项+新引擎+COUNT优化+测试+原型+文档
52ca673  fix: 等级百分位口径统一+Profile等级行Lv前缀+等级详情页标题
3811023  fix: 5项解题页遗留问题修复
5d3af37  docs: HTML原型添加 emoji→Material Icon 注释说明
7bcb802  fix: 积分显示3项修复 -- 枚举可读文本/等级编号/表头行
5ecf8fd  fix: 统计页3项修复 -- level相对分档/TrendChart统计行/HeatmapChart时段提示
3e9c958  fix: forcePull 先推本地积压再拉取，弹窗增加空数据检测
e7ad139  fix: 积分流水表累计值改为每行逐行累积而非全量总计
20f8661  fix: seed脚本 update_or_create + 自动清理旧code
733a32e  chore: rebuild assets.db v12 — 22条成就定义
230d3e6  perf: 等级详情页百分位后台加载+初始缓存值，消除首屏闪烁
fe35d0b  feat: 审计测试用户全量测试数据脚本（62题/69积分/4组卷/30签到）
1e6f3d9  fix: 积分显示4项修复 -- 列顺序/时间格式/类型说明/等级页标题
4c6a151  fix: 同步完成后自动返回我的页面并刷新数据
4a7c7dd  fix: 作业功能批量修复 — 幽灵列清理/状态推算/本地优先/版本号修正
3e7635a  fix: 作业列表 course_ids 未缓存时先等 API，不显示未过滤的全量数据
5fa6c18  Revert "fix: 作业列表 course_ids 未缓存时先等 API，不显示未过滤的全量数据"
1127e3f  fix: 作业列表改用 API 精确缓存，秒开不再显示未过滤数据
b56e551  test: 补充 getPendingCached mock 实现
915d6f4  fix: 统计页9项修复 -- 等级百分位端点/正确率汇总/过滤对齐/降采样/性能/测试
77c7dfc  docs: 填空题揭示答案后增加正确/错误自评按钮（HTML原型）
0efa9f1  fix: 偏好加入同步队列 — 服务端PreferenceFilter模型+客户端入队+补全DDL+文档
dc1989e  fix: 偏好同步 handler 修复 — json序列化+client_id唯一键
11b9045  style: lambda→def 修复 flake8 E731
b5f3a9a  fix: 首页批量修复 — 签到锁死/连续天数/任务3改单调/填空自评
4a2ee45  fix: preference_filter schema 迁移缺失导致INSERT崩溃
c9d8c9c  fix: 筛选面板段描述 lastIndexWhere→indexWhere 导致永远显示压轴繁琐
fa31d10  fix: 积分单位归一化+签到做题积分+统计页显示修复 -- F-10/F-11/F-12/F-14/F-16/F-17
c6ccb0d  fix: 筛选段描述布局对齐 HTML 原型 — 每段独立行
e08145e  fix: TrendChart 折线图因缺少 width 约束出现竖线/空白 -- CustomPaint 宽度为0
aeb66a0  fix: 解题页10项修复 — 路由断裂/参数链路/UI对齐HTML原型
6f75afc  fix: 解题数据管道修复 — 完成链路/积分动态/source归位
45af4d4  fix: 折线图数据点<2时显示'暂无数据'而非空白 -- _TrendPainter points.length<2 直接return
ee9b708  fix: 回退 addPostFrameCallback — 导致编辑偏好永远加载中
283bb3e  fix: 积分流水页批量修复 — source分类修正/同步链路补齐/文档同步
c830dbf  fix: 解题目系统三级修复 — 索引分层/状态推算/存档写回
f145dae  fix: TrendChart 增加 Y轴刻度/网格线/X轴日期标签 -- 对齐HTML原型
bf62611  refactor: 积分存储从厘分(INTEGER×10)改为分(REAL直接存)
cecb39d  fix: 服务端积分分类对齐设计文档 -- PRACTICE_REWARD为唯一earned，其余归bonus
d636876  fix: 解答题按小问统计正确率 — 两端DAO统一口径
97cf5c6  fix: 解题步进越界+完成条件按方法检测
93a4bbb  fix: 厘分改分后发现的 4 个回归 bug
4ef11cc  fix: 3项成就系统修复 -- 实时计数+upsertProgress+%后缀+排序
a45d171  chore: rebuild assets.db v14 — label修复+排序修正
56e304a  chore: 种子脚本flake8合规 + HTML原型描述同步
e1160f8  refactor: lecturesDb → coursesDb（Flutter 端）
c15fdbc  refactor: lecturesDb → coursesDb（服务端+测试）
f1ca970  chore: 删除旧的 lectures_database.g.dart
d3638b5  docs: 同步 lecturesDb→coursesDb 改名到文档
e5430ca  fix: admin.py LECTURE_TABLES→COURSES_TABLES + tools.html 讲义→课程
24adee2  fix: LECTURE_TABLES→COURSES_TABLES 遗漏（build_schemas.py L263）
97ba506  fix: 选择/填空解题页4项修复 — 概念标签/自评结果/存档创建/mode推算
3ee3f56  fix: 解题页8项UI修复 + assets.db重命名遗漏
e0d6080  筛选面板重构：加题型筛选 UI + callback 改为 FilterState 对象
bd6f850  fix: 解题地图 completedSteps=0 + 同步推送 400 + amount=0积分跳过
9d5804f  fix: 解题地图页修复 — 状态标签/单存档重做/AppBar标题/批量DAO/测试
2e14865  feat(data): ConceptTagNode/KnowledgeCardGroup 数据层 + ExamRepository 树/分组构建
e9d711c  feat(filter): ConceptTagTreeView 树状概念标签组件
834e835  feat(filter): KnowledgeCardGroupView 分类知识卡片组件
21de639  feat(filter): FilterPanel 集成树/分组 + 默认全选 + 摘要行
15877dc  fix: 同步引擎批量修复 — serializer缺失points_transaction/文档同步/UI映射/cleanup优化
dfd50ae  fix: 步骤页 isRevisit 按 subQ/method 过滤 — 修复跨子题 stepNumber 碰撞锁死
9c78ec4  fix: 完成检测/状态推算按 subQ+methodId 过滤 stepNumber 碰撞
b8edf8a  feat(filter): 父页面适配 + 知识卡片分组Wrap修复 + 测试更新
40400a4  fix: 成就/统计步骤分组缺 methodId — stepTotal 多方法下少计数
cee5b8e  fix: 地图→步骤页路由 subQ index off-by-one — sortOrder 1-based 误作 0-based step页下标
1c56172  fix: submission_detail 加唯一索引防重复存档 — schemaVersion 3→4
dcfe649  fix: 填空题自评反馈整合到答案banner内 — 对齐HTML原型单个容器
66c71d5  新的数据库
36a45f5  fix: unlockedCount委托getSummary，消除Profile页与成就页计数不一致
6f88936  docs(filter): 同步筛选面板 Phase 2 设计文档和HTML原型
2a90173  fix: 同步系统第二轮修复 — pull DDL浮点精度/时间戳保留/幂等保护/server_id通用化
f3a5079  style(filter): 筛选面板视觉优化 — 7项改动
42560bf  fix(filter): 三项修复 — 偏好层级/池统计独立/宽度对齐
e4070a1  fix: InsufficientPoolException 显示 Instance of... 问题
300a779  fix(filter): 全选概念标签/知识卡片时传空集避免关联表过滤
8298cf1  fix: step_feedback/card_feedback 推送 500 — 粒度断裂导致 detail_cache 空
bb27d00  fix(recommend): 推荐页4项修复 — GlobalKey绑定/Pill图标/推荐原因独立行/预设默认项
3be2e3c  fix: 填空题自评按钮 Row 缺宽度约束导致布局崩溃 — 加 stretch
c0391bc  fix(recommend): 推荐页4项修复 — GlobalKey绑定/Pill图标/推荐原因独立行/预设默认项
d84a1ac  fix: 组卷消耗积分修正 — 智能组卷1→20, 自主选题2→20
50d5c36  fix: 填空题查看答案误触回顾模式 — 拆出独立_isReviewMode
bd7cd49  fix: SizedBox(w:Infinity)在Column(stretch)内仍传递无限宽——改用FractionallySizedBox
bd4af1c  fix: fill路由到choice页 — ExamQuestionCard缺questionType默认choice
deb8c50  fix(recommend): 推荐卡片标题改用Text+maxLines替代substring硬截断
d914b71  fix: homework/question_history switch默认值solveChoice→solveMap, 对齐pageName
706081b  fix(solve): 四页布局崩溃 — 移除width:∞+borderRadius组合+改用CrossAxisAlignment.stretch
1aefc0b  fix(solve): 按钮无限宽崩溃 — SizedBox显式约束阻断传播链（同58ca4d7模式）
c7c4666  refactor(solve-reveal): 答案/解析/自评拆为独立卡片，删除_RevealResultBanner
5b4132c  fix(solve-reveal): 答案值改用MdLatexBody渲染LaTeX
b077d4b  fix(recommend-card): 标题改用MdLatexBody渲染LaTeX+ClipRect高度约束
7bc8786  fix(recommend-card): 移除ConstrainedBox高度约束 — MdLatexBody自然高度
a8afb1a  fix(exam): 智能组卷消耗改为10积分（误写为20）
53fd09a  feat: 抽取共享 QuestionCard Widget，统一 6 处题目卡片
f51882c  fix: applyFilter 未清空树/组选中状态→加载偏好时概念标签/知识卡片被静默吞掉
7547263  fix: RecommendCard 过滤 '偏好推荐' sentinel，避免显示无意义原因
fa2c6e6  refactor: 增强 ActionChipWidget 支持 active 态，替换 quicklook_other 私有 _actionChip
fa4ac9c  docs: 同步架构文档中 ActionChipWidget 的 active 态支持
94c2ca3  docs: 同步 Flutter代码规范.md 设计文档中的 Widget 清单和目录
ec9cd2f  feat: 创建教师端独立 Flutter App（题库浏览+讲义阅读+选题导出）
5bc1e5d  feat: 教师端功能增强和服务端对接
d43b5f8  feat: Web 端发布作业页新增粘贴选题 JSON 功能
59d3880  refactor: 移除发布作业页的组卷选择，仅保留 JSON 导入
a3d633f  cleanup: 移除教师通过学生端 API 看全部讲义的逻辑
8284cfe  cleanup: 移除教师端组卷相关历史包袱
9ef7460  refactor: 11个新写文件改为从学生端复制再修改
6e2e563  fix solving map: card titles, step label, archive UX, step_number data
87263b2  chore: 移除重复的 filter_panel.dart
4e835ad  fix: 修复 filter_panel.dart 导入路径
97f2c4a  sync HTML prototypes: remove fresh view, add retry button, drop retry from archive dropdown, step label by number
974c933  fix: 首次启动时从 bundle 复制数据库到文档目录
25fe060  fix: 重写 _buildTagTree 为递归构建，去掉死代码
e70ec52  fix HTML prototype: remove fresh view + startFirstStep, add goRetry
4b67d82  refactor: 13个文件改为从学生端复制再改
c907bc0  chore: 移除重复的 shared/question_card.dart
4863577  fix: 更新检查 API 路径错误
af358f8  fix: 更新提示从 SnackBar 改为 AlertDialog
3689357  fix: 更新弹窗改为从学生端完整复制
92ef88d  fix(teacher): 对齐学生端代码复用 — 文件命名/AuditLogger/QuestionCard/IP
7aaed7a  refactor: 12项UI割裂修复 — 共享status_style/AppColors常量/色板对齐/图标规范
f83f216  fix(teacher): 复制学生端共享组件 — QuestionImage/AppToast/AppPrefs/AppVersion
b380171  chore: 更新数据库 provider / sync update_manager / 数据访问层文档
674833a  fix: 6项UI割裂修复 — formatAmount去尾零/EdgeInsets常量/ExamHomePage Card/空状态
eb86ad9  fix(teacher): Future.wait隔离/死字段清理/难度渲染/静默异常日志
1fc522f  fix: 布局/色值/图标修复 — W-01卡片宽度/R-01热力图色值/F-23徽章图标
180b30b  fix(W-02): exam_auto_page 统一卡片水平宽度 — ListView padding 统一管控
c6bebf6  feat(teacher): 题库卡片支持点击查看详情（方案A）
cbe66aa  sync(teacher): FilterPanel卡片宽度统一 + question_bank_page布局对齐
8094290  fix(teacher): 6项UI割裂修复 — Card统一/EdgeInsets常量/EmptyPlaceholder/_typeLabel
8758550  refactor(teacher): 设置页section结构+预览页并行加载与修复
f19d5d4  fix(teacher): question_detail_page 8项修复 — Card统一/图片路径/步骤号/圆角
5784a70  feat(teacher): question_detail_page 补齐知识卡片展示
e4c6f40  fix: 每次 _load 时新鲜创建 Repository，避免 DB 替换后持有已关闭连接
398ede1  feat(sync): sync_queue 增强 — errorMessage 列+getPendingCount+limit500
4e3bba5  feat(sync): 同步进度弹窗差异化+失败重试+启动反馈
d692cb9  feat(sync): 同步状态全局可⻅ — 首页行+Tab角标+队列错误
8d0279b  feat(teacher): 同步教师端进度弹窗 — title/message+重试按钮
2274a1e  refactor(teacher): question_detail_page 按计划全面重构
461c616  fix: getUserInfo API结果回写本地缓存
b621117  refactor(teacher): question_detail_page 8项UI修复 -- 左边框装饰/去绿底/去重复
488ddd3  feat(scripts): add run_fix.py framework for safe DB fixes
899f9c3  docs: 关于页/设置页新设计 + 命名统一（讲义→课程）
6694286  fix: 命名统一'讲义'→'课程'（启动banner+强制更新弹窗）
ba4e039  feat(about): 三段式重做 — 数据版本+用户同步+法律信息
3d60b07  feat(teacher): 设置页数据版本卡片+更新按钮+Tab角标
6ebb43a  docs(html): about.html 三段式更新 — 数据版本+用户同步+法律信息
52adff0  docs(html): 同步学生端原型 — 首页同步行+队列错误+登录失败提示
372e8f9  fix(about): 用户数据同步按钮增加说明文字消除误导
e92e248  feat(server): 用户数据版本检测 — Student.data_version + API + push递增
0856a68  feat(client): 用户数据版本检测客户端 — Prefs+API+UpdateManager+banner
23c42b9  feat(about): 用户数据改为版本检测模式 — 三库统一卡片
1d10e78  perf(teacher): QuestionDetailPage 先跳转再加载，避免过渡动画掉帧
98b43e6  fix(qbank): strip ABCD from choice stems, strip artifacts from sub-question stems
2d84cbc  refactor: DAO 构造从缓存 DB 实例改为通过 DatabaseProvider 懒获取
004616c  fix(qbank): replace plain _____ with LaTeX underline in fill stems
43b2a91  fix: _checkOne 加 try-catch 防止单类型失败级联到所有版本检查
81a315c  fix(server): UserVersionCheckView 返回 schema_version 防止 fromJson 崩溃
934f2ea  fix: UserVersionCheckView 不调用 pull_user_db（太重）+ runUpdate 对 user 特殊处理
abc31e2  fix: UserVersionCheckView 不调 pull_user_db + runUpdate 对 user 特殊处理
f788c5a  fix(assets): flatten question images to fix Flutter asset bundling
e074266  fix(teacher): add question image assets to teacher app
3989a3e  fix(teacher): rebuild assets.db with flat image paths
aa9cc05  fix: markdown rendering data + code fixes
c1744af  feat: move images to documents dir for in-app update support
c620343  fix: teacher app compile errors after image migration
09184f3  chore: fix lint warning (unnecessary braces in string interpolation)
8cdab95  fix: remove archive dependency, implement manual tar.gz extraction
8b1cfa8  fix: smart stem truncation avoids unclosed \$ in formulas
aa74ecd  chore: update pubspec.lock and generated plugin registrant after removing archive dep
1ad86fc  Revert "fix: remove archive dependency, implement manual tar.gz extraction"
a0f7ac1  fix: remove _ensureDefaultDb 'copy once' guard, always overwrite on startup
7ee02c6  fix: add default size constraints to QuestionImage
1bdbf7f  chore: 首次发布前 App 基本信息配置 + 图标草稿
179a7c6  fix: init AuditLogger in teacher main.dart + update pubspec.lock
03a5b59  fix: version-based _ensureDefaultDb, preserve in-app update data
2f32160  chore: remove unused dart:convert imports
83b5e8c  revert: restore _ensureDefaultDb 'copy once' logic, remove version-file approach
32a3f74  revert: remove images-to-documents architecture (c1744af), restore original Image.asset mechanism
3b30d36  fix(teacher): 删无用搜索框 + 详情页传递选中状态
783a445  style(teacher): 筛选面板优化 — 来源默认折叠 + 排序移到底部
5395440  fix(teacher): 排序不起作用 + 删 Divider
2d15225  fix(teacher): 全选/取消全选按钮动态切换
403b433  fix(teacher): 筛选空语义修正 — null=不限/空列表=无匹配
246aa91  feat: 教师端添加 Android/iOS 平台 + 基本信息配置
5ecf879  fix(preference): 编辑链路断裂 — 编辑操作不再创建重复记录
baa4420  fix(cache): 2项运行时缓存问题修复
f958f08  refactor: 筛选子widget统一到widgets/shared/ + 学生端补全选/取消全选
f7975d2  fix: 页面返回刷新补齐 + dbVersionNotifier 覆盖全部 Tab
4391079  fix(sync): enqueue 后自动触发推送，不再死等
0e6eacd  fix: math rendering & data cleanup
18c95a6  fix(android): 修正 MainActivity 包名/目录 + Gradle 镜像/Kotlin 增量编译修复
bcf3bc3  feat(teacher): 发布准备 v1.0.0-alpha.1 + Android 构建修复 + MSIX 配置
ff053b8  feat(landing): 下载按钮链接到 Gitee 发行版 v1.0.0-alpha1
12edade  refactor(landing): Windows 移除弹窗直链下载，iOS 点击弹出未就绪提示
76842ea  feat(landing): 内部下载页，无公开入口链接
475662c  feat(landing): 新增百度网盘备用下载 + 内部页视觉重构
6043ee7  refactor: 着陆页重塑 — 价值观卡片为主体，去除 Hero，压缩下载和联系方式
bf46d17  style: 着陆页质感提升 + 完善响应式 - 价值观卡片加左侧主色装饰条 + hover 上浮 - 标题加蓝色下划线装饰 - 反对/主张加 ✗/✓ 前缀（CSS 伪元素） - 联系方式背景改为浅主色调 - 下载链接行包裹为白色卡片 - 容器四挡断点：480→580→640→720px - 窄屏 <400px 单列，宽屏 ≥900px 增大间距
cc5081f  fix: 补充网盘链接和微信号
2583ae1  fix: 更新微信二维码（带联系方式 zhangyubb101）
bc192f4  chore: 用 qrcode 库重新生成干净微信二维码
784246f  cleanup: 移除旧 wechat-qr.jpg，已替换为 PNG
f037d72  fix: 二维码加 ?v=2 绕过 Cloudflare 缓存
0b11d54  index on master: f037d72 fix: 二维码加 ?v=2 绕过 Cloudflare 缓存
75dd528  On master: wip before perf fix
5ab54a9  feat: 新手体验改进 — 快速练习 + 引导卡片 + 空状态引导文案
ddd47ec  fix: 14项性能优化 — SQL聚合替代全表扫描+N+1批量查询+乐观更新+executemany
c28bb06  chore: 统一版本号 v1.0.0-alpha.1+1 + 过渡图标 + 版本号自动生成
478b7be  fix: 6项第二轮性能修复 — 服务端N+1/统计页并行/幽灵方法/profile优化
db57af6  fix: 4项教师端性能修复 — 全表扫描/重复查询/幽灵方法/同步遗漏
8bb4603  fix: T-02 preview_page N+1 — 批量 getQuestionDetailsBatch (7N→4次查询)
c5c8302  hotfix: customSelect 表名 question（单数）而非 questions（复数）
f4a5143  fix: MarkdownBody selectable:true 拦截点击事件，导致题库卡片文字区域无法进详情
1ccdd33  fix: 5项题库性能优化 — 随机抽取/SQL统计/分批保护(两端同步)
850cbb3  docs: App基本信息 — 版本号/包名等身份信息文档
61b4a79  fix: app基本信息逐项修复 — 窗口标题/Android版本/iOS+macOS图标/splash/Generated.xcconfig
f240d93  fix: generate_icon.py 路径修正 + iOS/macOS/splash 图标重新生成
e2de018  chore: 版本号更新 1.0.0-alpha.1+1 → 1.0.0-alpha.1+2
5959cae  fix: main.cpp 编码 UTF-8 BOM，修复 MSVC 中文编译错误
7253a85  fix: ICO 多帧构造错误，Windows 任务栏图标不更新
cd39368  refactor: preview_page 复用 QuestionCard 替代内联 Text 渲染题干 LaTeX
9237022  feat: 管理员仪表板 — 今日概况卡片 (活跃用户/做题/同步)
ebd835f  feat: OperationLog 运行日志 + 导出按钮 + API 拦截日志
be4c46f  fix: 26 页面错误提示友好化 + OperationLog 集成 (原 _error=e.toString() 改中文)
b8a837c  整理docs
5bcad01  chore: 补提交 4 页面友好化 + 教师端 assets.db
57f0083  fix: 子代理修正 7 页面的 OperationLog import 路径
c22a2c6  feat: 导航日志 — GoRouter observer 记录页面切换
c2145da  fix: OperationLog 全覆盖 — 教师端零突破 + 学生端7页面 + 导航日志
f59570d  feat: 签到操作日志
2032534  chore: 补提交子代理对教师端/学生端剩余页面的 OperationLog 修改
10ed37f  fix: 登录页/教师端导出按钮 + main_shell OperationLog
c22b3b0  feat: 关键操作 action 日志 — 注册/做题/评分/组卷
0ba2e11  docs: OperationLog 文档 + HTML 原型更新 (about/login导出按钮)
92c7359  fix: 日志导出改为剪贴板复制 + 按钮移到底部 (about/登录/教师设置)
913dc46  docs: 日志导出方式改为剪贴板
6213718  feat: getUserInfo 加后台刷新 + 新增 getCachedLevelPercentile
e1f7096  fix: rawSQL 清理 — 幽灵列 accessible_course_ids 移除 + .extra() 替换 TruncDate + schema 版本注释
4035df9  fix: 头像上传字段名 url→avatar + 上传后写回本地 user.db
0ce743e  refactor: 页面刷新机制重构
29bad5b  fix: 添加 WM_GETMINMAXINFO 设置窗口最小尺寸 600×400
8f87784  fix: 首页连续签到天数计算修复
4c34450  fix: 自主选题全链路修复
23eb904  fix: 快对答案 — 解答题多子题展开为多行 + 试卷信息卡片 + 补标题/题型渲染
ebd01b5  fix: 组卷公开私密/发现/收藏/预览全链路修复
5dbcad6  fix: 修复5页exit rating弹窗死代码(canPop:true->false)+概率调为5%
dce35a1  fix(teacher): 教师Web端横切探查修复 — 10项
9874e48  feat: 补充4处积分反馈Toast(任务/签到/评价)+移除未用变量
d23a137  fix: 新人赠送弹窗改为读SystemConfig固定值,非总赠送积分
bf1eb67  feat: 池子不足弹窗(SnackBar→AlertDialog+两按钮)
01618f0  fix(teacher): 第2轮修复 — about/design-doc/学生correct-total
42b2e17  fix: 补齐 points_transaction.client_id 客户端 Drift schema（对齐服务端 DDL + 设计文档）
083874d  feat: 升级弹窗(新Widget+等级检测+签到后检测)
ce51de0  feat: 更新完成Toast + debug.html删除更新日志区块
9f973e6  fix: token刷新死代码 — 异常处理器未返回40002
1a24a40  fix: 组卷收藏/预览第二轮修复
fe2f008  fix: tryRefresh 不保存新 refresh token — 二次刷新必败
147d617  fix(student): refresh 后不保存新 refresh token — 二次刷新必败
87d464b  feat: 成就解锁弹窗+文档清理
32cf159  fix(teacher): 部署CSS丢失6个样式类 — paper-card/radio/search-box/username/detail/tag
2bd0618  Revert "fix(teacher): 部署CSS丢失6个样式类 — paper-card/radio/search-box/username/detail/tag"
6d05efb  fix(teacher): students.html 忽略 URL 参数 class_id
8d04b50  fix(teacher): 6项UX问题修复
1e189e4  fix: 关于页 Column+Spacer 溢出改用 SingleChildScrollView
2aaa8f4  关于页用户数据 tile 重命名为多设备同步数据
53b8f6a  feat(admin): 系统工具页增加积分赠送功能
6145c37  fix: 解答题子题拼接改用引言提取+SubQuestion权威来源
fa9aecb  fix: repair CI — align test mocks with source API and tune Django deploy check
520b095  fix: 补测试缺口 + 修复 CI 配置 —— F-01~F-07/F-10/F-12
3175237  fix: 修复 4 个服务端测试断言与 fixture 不匹配
d05174c  Windows安装包构建文件
82495d2  refactor: 抽取 shared 共享包，消除两端 17 对重复组件
ed6f20f  chore: shared 包 .gitignore 补充 pubspec.lock
6af9635  fixup: 从 git 恢复 5 个共享文件原始内容，仅改 import 路径（取代重写导致的 API 错误）
703849e  fixup: 补 shared 抽取遗漏 — app_version/layout/loader/teacher-sort
af75999  chore: bump version to 1.0.0-alpha.2+1
6d5c5d3  feat: 版本号同步脚本支持更新 .iss 安装包版本号
8f70eec  fix: 补齐 release 构建缺失的 Android 权限
37a458e  fix: 静默失败修复（P0）+ 测试修复（P1）
1b674f8  fix: P2 测试文案适配 widget 实际渲染
280d730  fix: 修复 release 构建 Android 版本号显示为 null
54e7d5b  refactor: generate_version.py 停止生成死代码，只维护 shared 单源版本文件
a45796e  fix: PopScope 退出评价弹窗条件不满足时页面卡死 — onPopInvokedWithResult 无条件 pop
822754e  fix: emoji 环境限 + 文案 mismatch 修复
d527c7a  fix: FilterPanel horizontalMargin=0 — 父容器已有 padding 时避免左边距重复
7904656  fix: 批量修复 — 按钮快速点击防护/清理shared重复副本/版本号同步文档
e80d250  fix: 收尾修复 — 文件锁 + solve_map_page 空数据视图
54a4fa7  fix: 编辑已有偏好时 FilterPanel 全选覆盖 — applyFilter 调用时序竞争
4a57ff5  fix: 关于页版本检查失败提示 + ConnectivityMonitor 初始状态检查
144e417  fix: FilterPanel 空维度提示 — 当某维度全未选时显示警告标签
f70336b  refactor: 日志导出从剪贴板改为系统分享面板 (share_plus)
3378381  feat: 概念标签树父子联动 + 知识卡片组全选/取消
a6a236d  chore: withOpacity → withValues 消除 deprecation warning
d7eb6ed  fix(solve): 选择题/填空题重新作答后结果条不消失、无法提交
db5e1ff  fix: 日志导出失败——share_plus 降级到文件导出+Explorer
e858161  feat: 导出文件名加时间戳，避免覆盖
6c8d5c7  fix: applyFilter 清空 _selectedConceptTagNames 导致编辑偏好时标签丢失
f754b77  fix: 概念标签/知识卡片 onChanged+selectAll 缺同步另一集合
73c9af4  fix: sync push stuck and stale version banner
ce10a01  fix: 偏好摘要过长 — 年份/地区/标签缩略 + 展示限行
0a0bb51  fix: 填空题自评竞态条件 — 乐观锁定阻断并发点击
fdad26d  fix(solve): 填空题 SolveRevealWidget 纯受控化，消除重新作答后答案残留
d691c2a  chore: share_plus 10.1.4→13.2.1 消除 KGP 警告
54e4d95  默认 wal_autocheckpoint=1000（每~4MB自动 checkpoint），防止 WAL 膨胀
cf4292d  fix: Android 日志导出先走系统分享，不写 Downloads
5f8a4a6  chore: 网页下载链接更新到 v1.0.0-alpha2
674721f  fix: Gitee release tag 是 v1.0.0-alpha.2+1 不是 alpha2
c402d9a  临时文件提交
cf7c4cb  fix: 解答题子题改用<br>拼接+连续编号+不移除表格
e9de2d1  fix: 子题编号用原序号+Markdown表格转HTML
af74f7a  fix: stem中\\n转<br>实现换行+表格内\\n保护
67645cc  docs: 项目编年史 5 篇完稿（总览/v1/v2/Agent统计/模式总结）
```
