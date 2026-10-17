# 案例全文

当前89例，其中89例已补充逐项研究。已查阅资料仍可能未披露部分信息，具体见各条缺口；不将推断当作真实实现。

## 1. Canada Goose：旺季查询自动化与语音转人工导购

国家：加拿大；项目落地：未披露
行业：高端服饰零售与客户服务
国家口径：总部国家：Canada Goose Holdings Inc. 的2026年5月监管文件列主要行政办公室在加拿大多伦多。项目未列实际上线国家；“全球扩展”不等于所有市场已部署。

概述：用Agentforce处理订单、保修与常见查询，按购买意图将顾客交给真人Style Expert。

流程：消息或来电进入→识别意图并查询企业数据→处理常规问题→销售意图或复杂问题转给真人。

落地程度：已上线：官方记载数字渠道2025年10月底启用、12月语音试点；具体国家与全面上线日期未列。

人工职责：真人Style Expert承担购买建议与个性化服务；客户团队、Salesforce和NeuraFlash共同交付。Calvin Ng自述先负责知识事实依据，后参与交付领导。逐项代码归属及持续运维分工未公开。

证据说明：官方作者页确认Ankit Chaudhari为Product Forward Deployed Engineering总监，且署名Canada Goose案例；Ashwin Bijani项目帖明确实施由Ankit牵头，Ankit在评论中确认其代表本团队。项目级牵头证据来自参与者公开帖，保守列B。

可切入环节：分析：先做经过身份核验的订单状态查询，保留购买意图转真人；把正确查单、越权拒绝及转接完整性作为上线门槛，再扩到保修与语音。

- 目标常规消息查询解决率：89%。口径：官方指标页明确为routine messaging inquiries，非全部联系量或语音独立解决率；样本和评判方法未知。

- 全渠道整体分流率：23%。口径：完整案例自报；原始分子、分母与精确统计窗口未给出。

- 旺季等待时间：下降13.9%。口径：官方指标页自报；未列原分钟数、均值或分位数，也未独立拆出语音贡献。

- 客户满意度CSAT：3.3→4.0（相对提升21.2%）。口径：完整案例数据；增加0.7个评分单位，非21.2个百分点。量表上限、样本与回收率未知。

- 整体交付周期：约3个月。口径：NeuraFlash参与者T. Brett Chisholm自报，含数字与早期语音交付；未给起止日期，不等同于语音试点单独工期。

- 投入、运行成本及净收益：未公开。口径：实施费、授权费、数据访问和通话费用、每次有效解决成本及增量收入未披露；不能用分流率换算现金节省。

### 介入前的问题与基线

- 【公开披露】旺季大量查单和保修查询占用全年专业团队，挤压个性化服务时间。 [来源1](https://www.salesforce.com/blog/canada-goose-voice-ai/)

- 【未披露】未公开介入前每类查询量、等待时间分钟数、人工单次处理成本及可比较的对照组。

### 工程师具体做了什么

- 【公开披露】Ankit的正式FDE职衔由官方简介确认；项目牵头职责由Ashwin具名说明，并有Ankit同帖回应。该链路强于仅凭供应商有FDE团队推定客户用了FDE。 [来源2](https://www.salesforce.com/blog/author/ankit-chaudhari/) [来源3](https://www.linkedin.com/posts/ashwinbijani_cnx26-connections26-salesforce-activity-7467753837362180096-qghp)

- 【公开披露】客户Calvin Ng负责事实依据知识并参与交付领导；NeuraFlash参与者称约3个月完成数字与早期语音上线。能确认协作，不能还原个人代码贡献。 [来源4](https://www.linkedin.com/posts/calvincarlosng_agentforceworldtour-agentforce-activity-7458355356960776192-orNt) [来源10](https://www.linkedin.com/posts/tbrettchisholm_during-dave-borrellis-fantastic-keynote-activity-7458563628766658560-yXXL)

- 【公开披露】Dennis Liut在上线帖确认先消息、后语音的推进顺序；伙伴NeuraFlash亦公开确认合作。 [来源5](https://www.linkedin.com/posts/maxcomparetto_agentforce-voice-ai-voice-agents-for-every-activity-7423045213138583552-8BtR) [来源11](https://www.linkedin.com/posts/neuraflash_agentforce-voice-ai-voice-agents-for-every-activity-7424177516455600128-Uc9g)

### 技术方案与数据流程

- 【公开披露】客户实际链路：Salesforce Voice with Amazon Connect接入Agentforce Voice；ElevenLabs承担语音识别与合成，转人工附会话摘要。 [来源1](https://www.salesforce.com/blog/canada-goose-voice-ai/)

- 【公开披露】Data 360以零拷贝接入OMS、ERP、POS、GCP及Microsoft Fabric；数百篇知识文章经索引与检索支持回答。 [来源1](https://www.salesforce.com/blog/canada-goose-voice-ai/)

- 【公开披露】每轮确定性注入约100字符的记忆变量，限制上下文增长；这不是完整上下文或模型最大窗口的大小。 [来源1](https://www.salesforce.com/blog/canada-goose-voice-ai/)

- 【公开披露】平台级技术背景：官方工程文介绍小模型意图分类与检索并行、WebSocket流式连接，以及识别打断后停止播报。部分内容在发布时仍属逐步推出，不能认定客户逐项采用。 [来源7](https://www.salesforce.com/blog/agentforce-voice-agent-technical-challenges/)

- 【分析／复现建议】复现建议：为订单、保修和知识回答分别建立工具契约；先核验顾客与订单关系，仅返回必要字段，明确数据时效和“未找到”分支。不要让生成内容充当查单成功证明。

- 【分析／复现建议】复现建议：记忆变量保存结构化事实而非自由改写；区分顾客更正、待答问题和已完成动作。用长对话、跨话题、订单号更改和中途打断测试状态丢失。

- 【分析／复现建议】复现建议：把语音拆成识别、检索、生成和播报计时，检查转人工时的摘要、订单标识和购买意图是否完整；设置检索超时和队列不可用的明确退路。

- 【分析／复现建议】复现建议：文本通过回归后再接语音，还应加入噪声、口音、拼写和多问题样本；文本正确率不能替代端到端语音验收。

### 解决程度与业务提升

- 【公开披露】官方指标页确认常规消息查询解决率及等待时间改善，但没有公开渠道分层、样本数或因果实验。 [来源6](https://www.salesforce.com/agentforce/metrics/)

- 【公开披露】官方展示页确认购买意图继续转真人；目标是把人工用于高价值服务，而不是最大化自动化比例。 [来源9](https://www.salesforce.com/customer-stories/agentic-enterprise-city/)

- 【分析／复现建议】效果解读：分流、等待时间和满意度应分别衡量。要判断是否增加收入，应比较相似客户的成交率、客单价和服务成本，而非把所有后续成交都记到AI名下。

### 尚未公开的信息

- 【未披露】未披露底层大模型及版本、提示词、检索排序参数、记忆变量字段、更新规则和上下文截断实现。

- 【未披露】未披露每个源系统连接方式、身份认证、租户与行级权限、语音录音保留、日志脱敏以及第三方推理的数据流边界。

- 【未披露】未披露误答、错误转接、人工重复处理率、语音端到端延迟、回归集和具体上线验收阈值。

- 【未披露】未披露实施和运行账单、单次有效解决成本、净节省、增量收入或可复算ROI。

- 【未披露】未披露FDE人数、驻场时间、伙伴工作包、生产值守责任、部署国家、云区域和全面推广日程。

### 关键技能
- 分析：零拷贝数据访问与客户身份权限映射
- 分析：知识检索、状态压缩及多轮会话评测
- 分析：电话路由、打断处理与人工接管
- 分析：按意图和渠道拆分效果及成本

### 风险
- 分析：订单和保修数据若身份绑定错误，会泄露另一客户的信息；零拷贝不能代替访问控制。
- 分析：压缩会话可能丢失更正、否定和未完成问题；应单测跨轮一致性。
- 分析：追求分流率可能误拦截购买意图，损害销售和高端体验；分流不是唯一目标。
- 分析：不同旺季、渠道和问题难度会影响前后对比，观察性指标不足以证明净收入因果增长。

### 限制
- 89%仅对应目标消息查询。业务约占总联系量三分之一的概述不足以复算23%，不能将两者相乘或认作语音结果。
- 正文既说语音由一类扩到三类，又说四类用例可迁移；阶段口径不清，不断言某日语音已覆盖四类。
- 社媒“本月上线”只有相对时间，不能替代明确的试点日期；聊天、试点、推广可能是不同阶段。
- FDE牵头与伙伴交付可同时成立；没有证据把成果全部归于某个人或单一团队。
- 平台技术文档仅说明可用机制；不作为客户已启用全部功能、具体模型或合规审计的证明。

### 来源
1. [Canada Goose语音AI完整实施案例](https://www.salesforce.com/blog/canada-goose-voice-ai/)
2. [Ankit Chaudhari官方作者简介](https://www.salesforce.com/blog/author/ankit-chaudhari/)
3. [Ashwin Bijani：Canada Goose实施由Ankit牵头](https://www.linkedin.com/posts/ashwinbijani_cnx26-connections26-salesforce-activity-7467753837362180096-qghp)
4. [Calvin Ng：知识事实依据与交付领导职责](https://www.linkedin.com/posts/calvincarlosng_agentforceworldtour-agentforce-activity-7458355356960776192-orNt)
5. [Max Comparetto上线帖与Dennis Liut回应](https://www.linkedin.com/posts/maxcomparetto_agentforce-voice-ai-voice-agents-for-every-activity-7423045213138583552-8BtR)
6. [Agentforce官方成效指标：Canada Goose](https://www.salesforce.com/agentforce/metrics/)
7. [Agentforce Voice技术挑战与架构机制](https://www.salesforce.com/blog/agentforce-voice-agent-technical-challenges/)
8. [Canada Goose Holdings Inc. 2026年5月Form 6-K](https://www.sec.gov/Archives/edgar/data/1690511/000169051126000010/cg6-kq4fy2026xwrapper.htm)
9. [Agentic Enterprise City：Canada Goose](https://www.salesforce.com/customer-stories/agentic-enterprise-city/)
10. [T. Brett Chisholm：NeuraFlash交付Canada Goose](https://www.linkedin.com/posts/tbrettchisholm_during-dave-borrellis-fantastic-keynote-activity-7458563628766658560-yXXL)
11. [NeuraFlash官方确认Canada Goose合作](https://www.linkedin.com/posts/neuraflash_agentforce-voice-ai-voice-agents-for-every-activity-7424177516455600128-Uc9g)

## 2. Chambers Gasket：订单状态自助查询与交期变更审批

国家：美国；项目落地：未披露
行业：定制制造与工业客户服务
国家口径：美国为主体所在地：公司官方联系页列芝加哥地址；案例未逐国披露客户或部署区域，deploymentCountries留空，不把主体国当实际部署国。

概述：订单状态答案分散在销售单、生产工单和财务记录，人工查询反复打断客服与高层。

流程：客户提交邮箱、采购单号和零件号→请求核验→关联Salesforce订单与生产资料→返回状态/物流信息→未发货订单按规则处理交期调整，提前交付转厂长审批。

落地程度：官方案例及客户负责人证言确认约四周进入生产；同时80%办公室员工在内部使用和测试，外部推广优先小客户。不是所有客户已全面使用。

人工职责：办公室员工参与内部使用和测试，客服牵头采用；提前交付请求交厂长批准，推迟交期可由系统直接办理。其他例外处理及逐次人工复核制度未公开。

证据说明：Plative官方FDE服务页将本项目直接列在“Proven Results, Real Impact”并链接具名全文，页面亦引用客户四周进生产证言；全文确认Plative与客户共同实施。属于官方FDE项目归类，未披露具名工程师或项目个人职衔。

可切入环节：分析：先接入单类订单的只读状态查询，再引入经过身份核验和审批约束的交期变更。

- 估计节约工作时间：每日2–3小时。口径：客户负责人及供应商自报，未公开观察期、计时方法或对照；不是每人每天。

- 办公室内部使用和测试覆盖：80%。口径：使用与测试混合口径；不能当所有客户生产采用率。

- 从讨论到生产：约四周。口径：客户负责人证言，未给起止日期和后续推广完成日期。

- 项目投入及现金节省：未公开。口径：工时估计未扣除软件、实施和运维成本。

### 介入前的问题与基线

- 【公开披露】业务数据已有Salesforce底座，但状态查询需跨销售、生产和财务记录；一天最多约六次询问，升级时会打断高层工作。 [来源2](https://plative.com/client/chambers-gasket/)

### 工程师具体做了什么

- 【公开披露】官方FDE项目区直接归类该案例；具体交付由Plative和客户共同完成，约四周进入生产。FDE页的通用驻团队模式与计费不能自动视为该客户合同。 [来源1](https://plative.com/what-we-do/forward-deployed-engineering/) [来源2](https://plative.com/client/chambers-gasket/)

- 【未披露】未公开项目人数、驻场周期、各工程师职责，以及现有Salesforce底座与本次新增工作的详细分界。

### 技术方案与数据流程

- 【公开披露】已披露输入为邮箱、采购单号与零件号；代理核验请求，返回订单状态、物流或生产进度。原文未披露认证算法和对象连接键。 [来源2](https://plative.com/client/chambers-gasket/)

- 【公开披露】未发货订单可检查生产状态；推迟交期由代理办理，提前交期必须厂长批准。未披露实际调用的API、Flow或Apex代码。 [来源2](https://plative.com/client/chambers-gasket/)

- 【分析／复现建议】复现建议，非客户已公开实现：为订单、生产工单及交期变更建立稳定关联；禁止仅凭可猜到的单号访问其他客户资料，将授权失败与查无订单分开处理。

- 【分析／复现建议】复现建议，非客户已公开实现：写操作前后记录原交期、新交期、批准人和业务版本；针对重复请求、审批超时、并发修改设计幂等和回滚。测试只读查询与写操作分别过关。

### 解决程度与业务提升

- 【公开披露】客户估计每天节约2–3小时，80%办公室员工在内部使用和测试；没有公开计时样本、独立对照或所有外部客户的采用率。 [来源2](https://plative.com/client/chambers-gasket/) [来源4](https://plative.com/what-we-do/salesforce/agentforce/)

- 【公开披露】应收账款催收是下一阶段计划，不能将预计回款改善记为已交付收益。 [来源2](https://plative.com/client/chambers-gasket/)

### 尚未公开的信息

- 【未披露】底层模型与版本、是否使用RAG、工具编排、缓存、数据刷新与冲突处理未公开；不得据Agentforce品牌补出具体架构。

- 【未披露】错误回复率、越权测试、交期变更错误率、人工升级比例及持续评测集未公开。

- 【未披露】项目费用、许可证、推理费、维护和复核人力及现金净节省未公开；节省工时不能直接等同裁员或利润。

### 关键技能
- 分析：Salesforce跨对象关联与权限
- 分析：业务动作及人工审批设计
- 分析：订单状态与写操作回归测试
- 分析：客服采用和渐进推广

### 风险
- 分析：输入字段不足以确保身份时，订单或财务资料可能越权泄露。
- 分析：错误或重复交期变更可能影响排产和客户承诺。

### 限制
- FDE证据是官方FDE页面对具名项目的直接归类；案例正文没有逐人确认FDE职衔。
- 节约2–3小时属于客户估计，80%包含内部测试；未证明全量外部上线。
- 应收账款催收和回款改善属于下一阶段计划。

### 来源
1. [Plative：Forward Deployed Engineering](https://plative.com/what-we-do/forward-deployed-engineering/)
2. [Plative：Chambers Gasket客户案例](https://plative.com/client/chambers-gasket/)
3. [Chambers Gasket官方联系地址](https://chambersgasket.com/contact-us/)
4. [Plative Agentforce实施与组件说明](https://plative.com/what-we-do/salesforce/agentforce/)

## 3. Rectangle Health：Rex知识库客服与实时转人工支持

国家：美国；项目落地：未披露
行业：医疗支付软件与技术支持
国家口径：美国为主体国：公司官方高管介绍列纽约州Valhalla总部，现网页页脚列White Plains地址，均为美国。本案例未公开实际使用国家、数据中心或部署区域，不能将客户市场或总部当部署范围。

概述：收购后客服需覆盖多产品，经验分散且常见问题回答不一致；客户希望自助解决重复咨询。

流程：客户提问→Rex依据既有知识库解释退款、排查连接和指导报表→未解决或请求真人时进入Digital Engagement→检查客服在线状态→转接或提供邮件、电话、建单选项。

落地程度：官方具名案例报告Rex已用于客户支持，并在标题称每月数千次支持互动；上线时间、持续观察期与全量客户覆盖未披露。

人工职责：客户团队在上线前建立内部知识文档，技术支持负责人参与实施；复杂问题或客户主动要求时由真人客服接手，客服非全天在线。知识维护责任和抽检比例未公开。

证据说明：Plative官方FDE页面在“Proven Results, Real Impact”直接列出Rectangle Health并链接本项目全文；全文披露Plative协同实施Rex及两项定制转人工组件。角色依据是官方FDE项目归类，未披露具名FDE个人。

可切入环节：分析：从资料完整的一条产品线和常见问题开始，同时上线明确的人工升级与无人在线兜底。

- 月支持互动规模：数千次。口径：来自案例标题；未给精确数量、月份或成功解决占比。

- 重复问题自动解决率：未公开。口径：80%是计划达到的目标，不能用作已测得分流率。

- 总体支持成本变化：未公开。口径：仅定性称减少第三方支持依赖，未公开合同、软件消费和维护费用。

### 介入前的问题与基线

- 【公开披露】多次收购带来多条产品线，客服依赖个人经验、缺少统一复用办法；上线前客户已投入建设结构化知识库，这是Rex的重要前置条件。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)

### 工程师具体做了什么

- 【公开披露】官方FDE项目展示区具名链接本案例；Plative与客服团队协同实现Rex，并将两种自有组件接入，客户负责人称按时交付。 [来源1](https://plative.com/what-we-do/forward-deployed-engineering/) [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)

- 【未披露】项目团队规模、实施工期、驻场方式、知识清洗分工和逐人FDE职衔未公开。

### 技术方案与数据流程

- 【公开披露】Rex使用既有知识文章提供退款说明、硬件连接排障和报表指导；退款场景原文是解释，不代表自动执行退款。底层模型和检索实现未披露。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)

- 【公开披露】项目使用Agentforce to Live Agent，在未解决或客户要求真人时，经Salesforce Digital Engagement升级；通用组件页佐证其知识型排障和人工衔接能力。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/) [来源3](https://plative.com/what-we-do/products/agentforce-to-live-agent/)

- 【公开披露】项目使用Live Chat Escalation检查真人客服工时和在线状态；无人在线时给邮件、电话或建单选项。组件说明亦确认该路由机制。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/) [来源4](https://plative.com/what-we-do/products/agentforce-live-chat-escalation-agent/)

- 【分析／复现建议】复现建议，非客户已公开实现：将知识文章标记产品、版本、有效期与适用客户群；测试相似名称跨产品误召回，缺少支持依据时升级而非补猜。

- 【分析／复现建议】复现建议，非客户已公开实现：用真实历史问题同时评估答案支持率和转人工成功率；覆盖夜间无人、排队状态变化、用户重复请求等情形。分开统计发起互动、解决问题和再次来访。

### 解决程度与业务提升

- 【公开披露】案例标题报告每月数千次互动；正文描述全天自助回答并减少第三方支持依赖，但没有分流率、满意度或外包费前后值。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)

- 【公开披露】解决至少80%重复问题是最初目标，邮件与电话AI扩展是未来计划；两者都不能当作已实现结果。 [来源2](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)

### 尚未公开的信息

- 【未披露】具体模型、知识切分、索引、权限过滤、内容更新频率、转人工判定阈值与会话上下文传递实现未公开。

- 【未披露】未公开是否接触患者健康或支付敏感信息、数据保留及脱敏规则；不能因服务医疗行业就认定系统访问临床数据。

- 【未披露】真实解决率、错误率、人工升级率、等待时间和满意度基线未公开；每月数千次没有精确数量和统计月份。

- 【未披露】实施费、Agentforce消费、客服维护及第三方支持总成本未公开，不能计算净节省。

### 关键技能
- 分析：客服知识治理与检索评测
- 分析：Digital Engagement转人工集成
- 分析：在线状态与非工作时段路由
- 分析：支持质量与解决率口径设计

### 风险
- 分析：跨产品知识混用或过期文档可能误导退款及硬件排障。
- 分析：客服在线状态变化造成转接失败，或敏感信息随会话传递过多。

### 限制
- 官方FDE页具名归类构成项目证据，未公开工程师个人职衔。
- 80%是目标；每月数千次是互动量，不能当解决量或人工替代量。
- 邮件和电话AI扩展属于计划；退款能力在本例中是流程解释。
- 两项组件原链接失效后已核验现行官方产品正文；未观看成功的视频不用于断言技术配置。

### 来源
1. [Plative：Forward Deployed Engineering](https://plative.com/what-we-do/forward-deployed-engineering/)
2. [Plative：Rectangle Health的Rex客服案例](https://plative.com/client/rectangle-health-handles-1000s-of-support-interactions-with-agentforce/)
3. [Plative：Agentforce to Live Agent组件](https://plative.com/what-we-do/products/agentforce-to-live-agent/)
4. [Plative：Agentforce Live Chat Escalation Agent组件](https://plative.com/what-we-do/products/agentforce-live-chat-escalation-agent/)
5. [Rectangle Health官方：Scott LoPresti介绍及联系页脚](https://www.rectanglehealth.com/team/scott-lopresti/)

## 4. HappyRobot：合同PDF抽取与条款合规检索

国家：美国；项目落地：未披露
行业：企业AI软件与内部合同运营
国家口径：美国为总部国：HappyRobot官网链接的公司LinkedIn页明确总部为San Francisco，供应商案例也称其位于旧金山。该内部合同系统未公开实际部署国家或云区域，不以全球办公室推定多国上线。

概述：分处理者通知义务及其他关键条款埋在合同里，人工录入既耗资源又容易漏掉；公司不愿让产品工程团队转做内部工具。

流程：合同PDF→自动提取日期、金额与法律约定→映射Salesforce自定义字段→对话代理同时检索结构化字段与原始PDF→团队查询和核验合同义务。

落地程度：供应商官方全文明确系统已在生产使用，提供合同义务追踪和条款查询；未给上线日期、处理合同量或用户覆盖。

人工职责：HappyRobot团队查询合同并据条款核验义务，将内部工程资源继续用于客户产品。合同字段是否逐条人工批准、法务复核标准及对外通知审批未公开。

证据说明：Plative官方FDE页的“Proven Results, Real Impact”直接列出HappyRobot并链接合同项目；案例全文明确Plative设计Salesforce Agentforce双模块方案及已生产使用。官方项目归类成立，未披露具名FDE或人员配置。

可切入环节：分析：选一种合同及少数可验证字段，保留原文出处和人工校验，再扩展条款问答与通知义务追踪。

- 上线状态：已生产使用。口径：官方案例正文明确；没有公开日期、合同量或用户数。

- 每合同实际节省时间：未公开。口径：10–15分钟/合同是计划目标，未有上线后计时数据。

- 义务漏检率或法律风险下降：未公开。口径：没有评测集、漏检基线或索赔对照；不能把宣传措辞当100%正确。

- 总成本和净收益：未公开。口径：未披露实施、许可证、推理及人工复核成本。

### 介入前的问题与基线

- 【公开披露】客户需要把合同中的分处理者通知要求等义务系统化，避免逐份人工录入；选择外部实施，以免内部工程团队偏离面向客户的产品开发。 [来源2](https://plative.com/client/happyrobot/)

### 工程师具体做了什么

- 【公开披露】本项目由官方FDE结果页具名归类；Plative在客户现有Salesforce中构建两个模块，使CRM成为结构化合同信息的统一记录位置。 [来源1](https://plative.com/what-we-do/forward-deployed-engineering/) [来源2](https://plative.com/client/happyrobot/)

- 【未披露】未公开工程师姓名、人数、具体工时、交付阶段及是否长期驻团队；通用FDE计费介绍不能代替本合同。

### 技术方案与数据流程

- 【公开披露】第一模块解析PDF，抽取生效日期、合同总额、标志使用权及分处理者通知义务，写入Salesforce自定义字段供报告使用。 [来源2](https://plative.com/client/happyrobot/)

- 【公开披露】第二模块是检索增强生成（RAG）对话代理，同时参考结构化元数据与PDF原文。具体OCR、分块、向量库和模型版本没有公开。 [来源2](https://plative.com/client/happyrobot/)

- 【分析／复现建议】复现建议，非客户已公开实现：字段抽取需保留原文位置、合同版本、单位及币种；修订协议覆盖旧条款时维护显式关系，不将找不到条款解读为不存在义务。

- 【分析／复现建议】复现建议，非客户已公开实现：按条款类型建立标注集，将日期/金额准确率与通知义务漏检率分别验收；对否定、例外和跨段条件安排人工复核。

- 【分析／复现建议】复现建议，非客户已公开实现：读合同与发送通知设不同权限；只有得到批准的义务记录才能触发通知，记录批准人和发送结果，避免生成内容直接成为法律承诺。

### 解决程度与业务提升

- 【公开披露】官方明确系统已在生产，支持义务追踪和按具体条款查询；没有公开合同数、漏报率或已避免的法律索赔。 [来源2](https://plative.com/client/happyrobot/)

- 【公开披露】每份合同节省10–15分钟使用计划措辞，只是目标；不能宣称已实现，亦不能把营销中的不遗漏义务视为100%准确率。 [来源2](https://plative.com/client/happyrobot/)

### 尚未公开的信息

- 【未披露】PDF解析器、OCR、基础模型、提示词、检索索引、分块方式、字段验证与重试机制未公开。

- 【未披露】合同版本冲突、扫描件质量、异常条款、提取置信度、人工复核门槛和引用支持率未公开。

- 【未披露】是否已自动发送对外通知、通知渠道、授权审批与失败补偿未公开；已披露义务追踪不等于自动法律执行。

- 【未披露】项目费用、许可证、单合同处理成本、维护复核工时和实际净节省未公开；也未提供法律风险降低的可量化实绩。

### 关键技能
- 分析：PDF与合同条款结构化
- 分析：Salesforce字段建模和版本管理
- 分析：结构化与原文双路RAG
- 分析：义务漏检评测及人工复核

### 风险
- 分析：遗漏否定、例外或合同修订可能造成错误通知义务判断。
- 分析：敏感合同跨客户检索或未经审批对外通知会扩大法律与保密风险。

### 限制
- 本案例客户是HappyRobot自身，供应商是Plative；不是HappyRobot向其他企业交付的语音代理项目。
- 官方FDE页具名归类成立，个人职衔与投入未公开。
- 节省10–15分钟/合同是计划，不是测得收益；生产上线不等于已证明准确率和法律风险下降。
- 仅能确认义务追踪与查询，不推定自动发送通知、修改合同或作法律决定。

### 来源
1. [Plative：Forward Deployed Engineering](https://plative.com/what-we-do/forward-deployed-engineering/)
2. [Plative：HappyRobot合同合规案例](https://plative.com/client/happyrobot/)
3. [HappyRobot官方LinkedIn公司资料](https://www.linkedin.com/company/happyrobot/)

## 5. Arkeo AI：销售代理平台故障恢复与交接

国家：美国；项目落地：未披露
行业：企业软件与销售AI
国家口径：客户LinkedIn公司页自报San Francisco总部；不是实际生产用户或云区域证明。法律实体未另行核实。

概述：关键技术人员离职后，销售代理停摆且缺少文档；Streaver接管排障、恢复运行并交回维护能力。

流程：定位生产故障→修复代理与调度→补充监控和运行文档→加固发布及交接。

落地程度：供应商案例称三个核心代理已恢复生产并完成交接；未公开项目日历日期。

人工职责：供应商承担排障及交接期间值守；客户CEO参加复盘。生产用户动作的审批规则未公开。

证据说明：官方具名案例的项目服务栏目明确列Forward Deployed Engineering，FDE服务页也将Arkeo作为主要交付证明。属于供应商当前分类，未获客户独立确认。

可切入环节：分析：先恢复一条能验证完成的生产任务，梳理失败重试和状态写入，再扩大修复范围。

- 恢复的核心代理：3/3。口径：供应商自报ICP、Deal Notes、Pipeline恢复生产；非准确率。

- 救援与交接周期：约3个月。口径：供应商明确说时间线为事后重建，非提交记录精确计时。

- 可用性、客户转化与净收益：未公开。口径：缺少上线前监控基线、成本与独立对照，不能推算提升比例或ROI。

### 介入前的问题与基线

- 【公开披露】技术人员离职、缺少交接资料，三个销售代理停摆并影响新客户进入产品。 [来源1](https://streaver.com/case-studies/arkeo)

### 工程师具体做了什么

- 【公开披露】团队先恢复运行再整理架构和文档，随后加固并交接；项目页将FDE列为交付服务。 [来源1](https://streaver.com/case-studies/arkeo)

- 【公开披露】FDE服务页以Arkeo说明承担恢复结果及清晰退出责任，不仅提供人力。 [来源2](https://streaver.com/services/forward-deployed-engineering)

### 技术方案与数据流程

- 【公开披露】披露栈为Go、Python、TypeScript、Vue，AWS、Airbyte、Postgres，Sentry及GitHub Actions。 [来源1](https://streaver.com/case-studies/arkeo)

- 【公开披露】排障覆盖幂等、密钥处理与调度故障；补充限流、恢复、日志和部署维护文档。 [来源1](https://streaver.com/case-studies/arkeo)

- 【分析／复现建议】复现建议：为重试设置稳定任务标识，分别测试重复触发、部分成功及调度重启，并验证同一任务只产生一次业务效果。

- 【分析／复现建议】复现建议：交接验收由客户团队独立执行部署和故障恢复，记录失败步骤再补手册；这不是对本项目验收细节的陈述。

### 解决程度与业务提升

- 【公开披露】供应商称三个代理恢复生产，平台完成稳定化和文档交接；无前后可用性测量，时间线为重建。 [来源1](https://streaver.com/case-studies/arkeo)

### 尚未公开的信息

- 【未披露】模型、提示、检索、实际API、数据权限及密钥管理实现未披露；不能据技术清单推导完整架构。

- 【未披露】实际部署国家、云区域、项目日期、团队人数、测试集、故障率及运行成本未披露。

- 【未披露】未有客户独立确认、可复算利润效果或精确修复时间；页面提到产品转服务方向，未说明与后续路线的时间关系。

### 关键技能
- 分析：陌生代码逆向与故障定位
- 分析：幂等、调度及错误恢复
- 分析：监控、运行手册和能力交接

### 风险
- 分析：重复执行可能重复写入销售记录。
- 分析：只修表面异常会保留调度或状态一致性根因。
- 分析：恢复后若文档与权限仍集中于外部团队，可能重现人员单点依赖。

### 限制
- 周数是重建叙事：示意图将三代理均标第4周，正文说两个第2周恢复，故不采用逐代理精确周数。
- 供应商自报已交付；页面明确尚无客户创始人引语，缺乏独立验证。
- 20多个代理、Next.js/Vercel与Trigger.dev是后续可能路线，不写为已部署。
- 三个代理属于同一平台救援项目，只计一例。

### 来源
1. [Arkeo AI: Three AI agents restored in three months](https://streaver.com/case-studies/arkeo)
2. [Forward Deployed Engineering | Streaver](https://streaver.com/services/forward-deployed-engineering)
3. [Arkeo AI公司页](https://www.linkedin.com/company/arkeo-ai)

## 6. Hertz（赫兹）：从入站客服到主动续租与还车确认

国家：美国；项目落地：未披露
行业：汽车租赁与旅游出行
国家口径：美国是总部国家：Hertz 2026年官方新闻明确全球总部位于佛罗里达州Estero。项目资料没有披露部署国家、服务租客国家或云区域；集团160国经营范围不能当作本AI项目覆盖范围。

概述：Hertz先接入复杂入站客服，再复用业务连接主动确认还车时间、更新预订和办理延期。

流程：到期前一天触发外呼→确认还车计划→未接按规则重试→租客要求延期时变更租期或还车时间→记录结果并统计按时确认与延期情况。

落地程度：已上线；2026年3月已有主动语音客户证言，9月官方报道数千次外呼尝试。项目覆盖国家、总租客数和具体上线日期未公开。

人工职责：租客反馈预计还车时间；员工处理需要人工服务的互动。具体必须转人工的意图、逐笔审批制度和例外处理比例未公开。

证据说明：主办方AI Engineer完整逐字稿中，FDE CTO Sunny Rekhi在0:28确认身份，1:47–2:42用Hertz具体说明其前线部署工作与后端集成、主动续租；Decagon官方项目文章独立确认流程已运行。

可切入环节：分析：从到期前还车确认切入，先只读核验预订；验证身份、续租资格、价格确认与写入回滚后，再开放延期动作。

- 客服部署上线周期：6周。口径：官方伙伴培训自报Hertz较广客服部署上线速度；没有证明主动外呼单项工程也只用六周。

- 较广客服部署解决率：70%。口径：供应商自报；样本、窗口及渠道未知，非主动外呼接通率、续租转化率或正确性审计。

- 主动外呼尝试量：数千次（未给精确数）。口径：2026-09-02官方文章的数量级描述；不是独立客户数、全部成功通话或新增租单数。

- 项目投入与净收益：未公开。口径：未披露外呼带来的增量租金、净节省，或实施、订阅、通话和人工处理成本；平台最低交易规模不是本项目合同价。

### 介入前的问题与基线

- 【公开披露】Hertz最初希望把复杂的入站客服流程交给AI；在已建立后端连接之后，双方继续寻找可主动完成的客户沟通。没有可核验的原人工用时或积压量基线。 [来源1](https://ai.engineer/talks/7wu2hsRfvV0-forward-deployed-engineering-is-done-at-decagon)

- 【公开披露】客户视频说明还车计划变化需要更新预订并协调后续车队安排；自动化承接高量重复沟通，让员工保留需要人工关照的互动。 [来源6](https://www.linkedin.com/posts/thejessezhang_im-excited-to-share-more-on-outbound-voice-activity-7437527830722134016-GKjq)

### 工程师具体做了什么

- 【公开披露】Sunny Rekhi以Decagon FDE CTO身份，在介绍前线部署工作时直接用Hertz说明：先支持入站业务，再复用已有后端集成，主动联系租客办理延期。项目与FDE交付直接绑定，未披露具体工程师姓名或人数。 [来源1](https://ai.engineer/talks/7wu2hsRfvV0-forward-deployed-engineering-is-done-at-decagon)

- 【公开披露】这是从既有业务动作向主动触达扩展的项目；官方后续文章明确执行时点、重试、变更预订与记录结果，而非只发送租车提醒。 [来源3](https://decagon.ai/blog/campaign-composer)

### 技术方案与数据流程

- 【公开披露】Hertz专属已披露：复用已有后端集成，AI可在对话中办理续租。未说明预订系统名称、端点或事务实现。 [来源1](https://ai.engineer/talks/7wu2hsRfvV0-forward-deployed-engineering-is-done-at-decagon)

- 【公开披露】Hertz专属已披露：到期前一天触发电话；未接可重试；延期时延长租期或改还车时间，并将处理结果纳入平台分析。 [来源3](https://decagon.ai/blog/campaign-composer)

- 【公开披露】平台级说明，非Hertz逐项实施清单：AOP以自然语言定义外呼逻辑；Missions支持批量拨号、跟进和重拨；语音层识别人声/语音信箱及筛选器，并用turn detection与微调模型优化轮次和AOP执行。 [来源4](https://decagon.ai/blog/outbound-voice)

- 【公开披露】平台级说明，非Hertz采用证明：AOP可做Git版本管理和升级规则；集成产品支持API、MCP与SIP。不能据此补画Hertz的CRM、模型供应商或电话基础设施。 [来源7](https://decagon.ai/product/aop) [来源8](https://decagon.ai/product/integrations)

- 【分析／复现建议】复现建议：把租客身份校验、可延期资格、车辆可用性及价格确认作为确定性前置条件；写接口设置幂等键、审计日志与回滚，不能只让模型决定交易参数。

- 【分析／复现建议】复现建议：分别统计触达、身份核验、计划确认、预订写入和人工升级；以相似租单对照核算增量续租，并测试拒接、错号、语音信箱、重复重试和口语日期歧义。

### 解决程度与业务提升

- 【公开披露】官方报道确认已运行主动租车外呼，描述数千次尝试，并可区分按时归还确认与延期标记；没有公布接通率、实际延期量或还车改善幅度。 [来源3](https://decagon.ai/blog/campaign-composer)

- 【公开披露】供应商公开伙伴培训材料报告Hertz六周上线、解决率70%。该材料未分开入站与主动外呼，也未交代测量方法；仅作较广客服部署的自报结果。 [来源5](https://decagon.ai/modules/buyer-profile)

- 【公开披露】客户视频确认可按租客新计划更新预订，并将高量事务留给代理；员工时间转向高价值互动是定性证言，未给人时或裁员数据。 [来源6](https://www.linkedin.com/posts/thejessezhang_im-excited-to-share-more-on-outbound-voice-activity-7437527830722134016-GKjq)

### 尚未公开的信息

- 【未披露】未披露Hertz实际使用的基础模型/版本、语音识别和合成供应商、提示或AOP代码、检索系统与数据更新机制。

- 【未披露】未披露预订系统接口、身份核验、操作权限、价格授权、写入一致性、故障回退及强制人工审批规则。

- 【未披露】未披露客户触达同意、退订和当地呼叫时段的具体配置；平台合规宣传不能证明Hertz配置已通过专项审计。

- 【未披露】未披露外呼接通率、正确解决率、延期转化、车队利用率改善、CSAT因果效果或可复现测试集。

- 【未披露】未披露FDE人数/驻场时长、项目起止日期、实施与运行费用、净收益，以及实际部署国家和云区域。

### 关键技能
- 分析：事件触发外呼与有限重试编排
- 分析：租车API与预订写入一致性
- 分析：语音意图评测、人工升级与效果归因

### 风险
- 分析：误识别接听人可能泄露租车与行程信息；重试过密、未尊重退订或时区会造成骚扰。
- 分析：延长预订涉及车辆可用性和价格；重复写入、过期数据或模型误解日期可能影响本租客及下一位租客。
- 分析：主动续租可能增加收入，但没有对照数据就不能排除原本会自然续租的订单，亦不能由解决率推算ROI。

### 限制
- FDE认定采用B级：供应商FDE负责人在主办方完整逐字稿中直接讲述Hertz项目，另有供应商官方项目报道；不以客户logo或招聘职责推定参与。
- 6周和70%来自供应商伙伴培训材料，指Hertz较广的AI客服部署；未披露统计窗口、样本、渠道和独立核验，不能解释为主动外呼成功率。
- 官方客户案例页本次只解析到标题；业务细节以官方Campaign Composer文章及CEO发布的客户视频转录补齐。未独立复听完整客户视频。
- 演讲口语称car lease，官方项目文章明确car rental；本记录统一为租车续租/还车安排，不延伸为汽车融资租赁。
- AOP、语音模型、MCP及集成产品资料仅作平台技术背景；不声称Hertz逐项使用全部能力，或后来产品版本已应用于最初上线。

### 来源
1. [How Forward Deployed Engineering is done at Decagon：Sunny Rekhi完整逐字稿](https://ai.engineer/talks/7wu2hsRfvV0-forward-deployed-engineering-is-done-at-decagon)
2. [Hertz uses outbound agents to resolve issues before they arise](https://decagon.ai/case-studies/hertz-proactive-outbound)
3. [Introducing Campaign Composer: Proactive, compliant outreach](https://decagon.ai/blog/campaign-composer)
4. [Outbound voice: Scaling proactive customer engagement](https://decagon.ai/blog/outbound-voice)
5. [Decagon Partner Essentials：Buyer profile](https://decagon.ai/modules/buyer-profile)
6. [Jesse Zhang发布Hertz主动语音客户视频及转录](https://www.linkedin.com/posts/thejessezhang_im-excited-to-share-more-on-outbound-voice-activity-7437527830722134016-GKjq)
7. [Agent Operating Procedures (AOPs)](https://decagon.ai/product/aop)
8. [Integrations: Connect seamlessly with your existing support stack](https://decagon.ai/product/integrations)
9. [Hertz Showcases Employee Car Culture and New 2026 Fleet at Estero Headquarters](https://newsroom.hertz.com/press-releases/press-release-details/hertz-showcases-employee-car-culture-and-new-2026-fleet-at-estero-headquarters/)

## 7. Hernan Corporation Sdn Bhd：榴莲冷链订单、库存与交接协同

国家：马来西亚；项目落地：马来西亚
行业：食品制造与冷链物流
国家口径：马来西亚来自官方详细案例所述当地业务与运往KLIA的流程，代表已披露项目运营地。18个出口市场不是18国AI部署证明。总部具体地址尚未完成官网正文核验。

概述：把纸表、Excel和聊天中的冷链交接记录接回统一流程，减少重复录入与状态追问。

流程：员工上传订单或现场照片→Claude抽取并结构化→Lark更新记录、通知下游→异常升级与管理层查看。

落地程度：已生产使用；Claude合作伙伴目录将Hernan列为生产实证。

人工职责：员工拍照、上传、回答补充问题并执行实体作业；异常通知人处理。未披露每条自动入库记录是否经过人工批准。

证据说明：Agmo官方案例索引在FDE Case Studies栏直接列出Hernan冷链项目；详细案例和Anthropic官方托管伙伴资料确认工作流与投产成果。以项目级官方归类为FDE依据，不依赖客户logo或通用服务简介。

可切入环节：分析：从收货单图像转结构化草稿开始，验证品种、重量和单位后，再开放跨团队通知及写入。

- 订单录入用时：减少50%。口径：供应商及伙伴目录自报；样本、统计周期和分位数未公开。

- 收货记录处理：少于2分钟。口径：从码头照片到可追踪库存记录；不是单次模型延迟。

- 经营覆盖：49人服务18个出口市场，未增员。口径：项目时点的运营描述；未证明增加了18个市场，也未披露订单量变化。

- 总投入与净收益：未公开。口径：没有实施、模型、Lark、维护和复核成本；无增员不能换算成现金节省。

### 介入前的问题与基线

- 【公开披露】原流程依赖纸表、Excel、转发的WhatsApp消息，收货资料还需管理员重新录入，管理层获得状态存在延迟。 [来源2](https://agmostudio.com/claude-customer-story-hernan-corporation-puts-a-claude-agent-in-every-stage-of-its-durian-cold-chain/)

### 工程师具体做了什么

- 【公开披露】Agmo官方将本项目列入FDE案例专栏；详细交付涵盖将Claude接入Lark日常群聊，围绕订单、照片、库存记录及下游交接组织自动处理和异常通知。 [来源1](https://www.agmostudio.com/ai-case-studies/) [来源2](https://agmostudio.com/claude-customer-story-hernan-corporation-puts-a-claude-agent-in-every-stage-of-its-durian-cold-chain/)

### 技术方案与数据流程

- 【公开披露】项目明确采用Claude API的视觉能力和Lark群聊；员工上传文件或照片并提及助手，形成按等级和重量记录的库存数据，必要时追问。 [来源2](https://agmostudio.com/claude-customer-story-hernan-corporation-puts-a-claude-agent-in-every-stage-of-its-durian-cold-chain/)

- 【公开披露】订单事件触发下游通知；装货、检查和配送使用表单，差异、拒收及截单时间进入异常提醒，管理层收到实时汇总。 [来源2](https://agmostudio.com/claude-customer-story-hernan-corporation-puts-a-claude-agent-in-every-stage-of-its-durian-cold-chain/)

- 【分析／复现建议】复现建议：为订单和批次分配唯一ID；消息重试须幂等，低置信字段保留原图并转人工确认。

- 【分析／复现建议】验收建议：分别测字段正确率、重复入库率、漏通知率及异常处理时长；物理分级和放行仍需要明确责任人。

### 解决程度与业务提升

- 【公开披露】生产实证报告订单录入用时减半、照片转记录少于2分钟；49人支持18个出口市场且未新增人手。指标是业务步骤表现，不能视为模型精度或收入增长。 [来源3](https://partnerhub.claude.com/directory/partner/agmo-studio-sdn-bhd)

### 尚未公开的信息

- 【未披露】Claude模型名称、版本、调用路由、云区域及运行后端未披露。

- 【未披露】Lark数据表结构、API鉴权、重试机制、权限边界、审计和数据保留设置未披露。

- 【未披露】训练或微调、评测集、字段错误率、负载量、FDE人数与交付工期未披露。

- 【未披露】完整成本、毛利、损耗改善及其他国家实际部署未披露。

### 关键技能
- 分析：现场流程访谈与事件建模
- 分析：多模态字段抽取及单位校验
- 分析：协作平台写入、通知和异常管理

### 风险
- 分析：模糊照片、品种或重量误读可能污染库存。
- 分析：重复消息触发重复写入，或跨群通知泄露订单信息。

### 限制
- 供应商自报结果，未公开独立审计或错误率。
- 伙伴目录的通用预算、云平台、MCP和网关能力不等于Hernan项目使用配置。
- 不把自动读取等级与重量解释为视觉检测食品质量、温度传感器监测或自动判断冷链安全。

### 来源
1. [Agmo官方AI案例索引](https://www.agmostudio.com/ai-case-studies/)
2. [Hernan冷链项目完整案例](https://agmostudio.com/claude-customer-story-hernan-corporation-puts-a-claude-agent-in-every-stage-of-its-durian-cold-chain/)
3. [Anthropic伙伴目录：Agmo Studio](https://partnerhub.claude.com/directory/partner/agmo-studio-sdn-bhd)

## 8. Clio：应用内客服与Salesforce转人工

国家：加拿大；项目落地：未披露
行业：法律科技软件
国家口径：加拿大为客户总部所在地，官网隐私声明第1.1条明确总部在Burnaby。项目从北美扩展至全球客户，但未列具体国家；不把总部国当作AI托管地或全部部署地。

概述：让自助问答与人工接手形成连续客服流程。

流程：应用内提问→Agent Maven回答或转交→人工承接上下文→分析人员改进知识。

落地程度：已投产；先试点，再面向北美及全球客户推广。

人工职责：Clio坐席承接升级；专职AI分析员检查对话，修补知识和角色配置。

证据说明：完整官方客户案例的Solution段直接记载Maven FDE提供技术协助，并区分CSM与实施工程师角色，属于具体项目级FDE证据。

可切入环节：分析：优先做有明确答案的产品使用问答；复杂账户操作与法律判断应分别定权限。

- 聊天自主答复：超过80%。口径：正文口径；未披露样本与观察期，不能解释为全部客服渠道解决率。

- 相对旧机器人解决量：增加60%。口径：相对增长而非增加60个百分点；未给出基础数量。

- 人工技术支持速度：4倍。口径：归因于工单压力降低；未定义均值、分位数及计时起止。

- 完整经济性：未公开。口径：未公布采购、实施、模型调用、维护、复核成本和净节省。

### 介入前的问题与基线

- 【公开披露】旧规则机器人依赖预设答案和手工调整，重复咨询挤占复杂技术支持时间。 [来源1](https://www.mavenagi.com/customer-stories/clio)

### 工程师具体做了什么

- 【公开披露】六周上线期中，FDE按需技术协助；CSM统筹，实施工程师建设Salesforce集成并配置品牌语气及知识。没有把这些职责全部归给FDE。 [来源1](https://www.mavenagi.com/customer-stories/clio)

### 技术方案与数据流程

- 【公开披露】Agent Maven接入应用内聊天；不足99%置信的提问经Salesforce Messaging转人工，并携带对话和客户信息。Agent Designer用于检查与迭代。 [来源1](https://www.mavenagi.com/customer-stories/clio)

- 【分析／复现建议】复现建议：转人工事件使用关联ID，将用户身份、消息历史和升级原因分开授权；明确传递失败的回退队列。

- 【分析／复现建议】验收建议：固定产品版本和问题分布，分别测有依据答复率、错误自信率、升级成功率及重复联系率。

### 解决程度与业务提升

- 【公开披露】官方报告自助覆盖与人工处理速度改善；数字口径见指标栏，缺少独立对照。 [来源1](https://www.mavenagi.com/customer-stories/clio)

### 尚未公开的信息

- 【未披露】基础LLM名称、版本、路由、嵌入模型与向量数据库未披露。

- 【未披露】云服务商、托管区域、推理资源和数据驻留未披露。Salesforce是交接系统，不等同模型运行基础设施。

- 【未披露】置信分数来源、校准方法、评测集、审计结果及微调方式未披露。

- 【未披露】FDE人数、工时、合同价格、运行单价和净收益未披露。

### 关键技能
- 分析：知识治理与测试集设计
- 分析：CRM交接与权限映射
- 分析：置信分数校准及人工升级设计

### 风险
- 分析：高置信错误可能不触发转人工，应单独检查误答漏报。
- 分析：客户上下文流入第三方支持系统时，需要清晰的数据最小化和租户隔离。

### 限制
- 99%是转人工所用的置信门槛，不是经审计的答题准确率。
- “训练品牌语气与知识”未说明微调；不能据此认定修改了模型权重。
- 本条只覆盖客服；不将扩展中的销售、教育等流程当作同等成熟部署。

### 来源
1. [Clio客服完整案例](https://www.mavenagi.com/customer-stories/clio)
2. [Clio官方隐私声明](https://www.clio.com/uk/privacy/spain/)

## 9. K1x：税务软件应用内知识问答

国家：美国；项目落地：未披露
行业：税务科技软件
国家口径：美国依据客户官方联系页在新泽西Morristown的公司地址；该页未单独标注总部。本项目实际用户国家与AI托管地点未披露。

概述：将已有帮助内容转成产品使用中的自助答复。

流程：应用内提问→搜索知识内容及生成解释→支持团队查看问题趋势并优化知识。

落地程度：已投产；一周是接入交付时间，不是结果评估周期。

人工职责：支持团队继续完善内容与处理需人介入的问题；具体转人工路由、门槛未披露。

证据说明：Maven联合创始人署名官方FDE文章的Customer Impact: K1x段明确FDE嵌入团队、集成平台与部署应用内代理；完整客户案例补充原流程、界面和指标。

可切入环节：分析：从产品操作指南启动；税务结论、申报提交与资金动作需另设审核边界。

- 自主解决比例：80%。口径：供应商案例自报；结果观察期、样本、重开工单规则不详。

- 解决用时：通常少于3分钟。口径：原文为almost always，不能提升成100%或SLA；不是模型推理时延。

- 接入周期：1周。口径：官方FDE文章记载平台集成、文章同步和应用内部署；不代表完整前期采购周期。

- 完整经济性：未公开。口径：预算转配到服务运营岗位不等于披露现金净节省。旧厂商报价也不能替代Maven成本。

### 介入前的问题与基线

- 【公开披露】已有350多篇帮助文章，但旧机器人只能处理约15%咨询；报告能力也不足，人工仍忙于兜底。 [来源2](https://www.mavenagi.com/customer-stories/k1x)

### 工程师具体做了什么

- 【公开披露】FDE直接参与客户团队，一周内完成平台集成、帮助文章同步与产品内会话代理上线。 [来源1](https://www.mavenagi.com/resources/forward-deployed-engineers)

### 技术方案与数据流程

- 【公开披露】应用内instant answers同时呈现可搜索内容与生成式回答，提供操作步骤；上线后Maven继续协助提示优化，支持团队可查看常见问题趋势。 [来源2](https://www.mavenagi.com/customer-stories/k1x)

- 【分析／复现建议】复现建议：按产品、版本和权限给文章加元数据，保存同步时间与原文链接；过期内容暂停参与答复。

- 【分析／复现建议】验收建议：把一次解决、延迟重开和转人工分别计数；用同一时间窗、同类问题比较原机器人与新代理。

### 解决程度与业务提升

- 【公开披露】官方公布自主解决比例及处理速度改善，但不同增长指标未给出可对齐的基准。 [来源2](https://www.mavenagi.com/customer-stories/k1x)

### 尚未公开的信息

- 【未披露】基础LLM、版本、多模型路由、微调和检索实现未披露。

- 【未披露】云平台、部署区域、运行资源、向量库、数据驻留和租户隔离实现未披露。

- 【未披露】应用嵌入协议、知识更新频率、错误回退、人工交接集成与权限细节未披露。

- 【未披露】FDE人员规模、完整成本、可复现评测集和指标分母未披露。

### 关键技能
- 分析：知识同步与版本管理
- 分析：产品内嵌问答界面
- 分析：意图分类与客服效果归因

### 风险
- 分析：旧版本帮助文章可能给当前产品提供错误步骤。
- 分析：用户可能把软件操作提示误当税务意见，需要明确答复边界。

### 限制
- 案例另称解决量10倍、解决率6倍；但约15%到80%不直接等于6倍，未公开统一基准或分母，因此不自行拼成同一测量序列。
- ChatGPT-style是界面描述，不能当作OpenAI或GPT模型使用证据。
- 税务软件客服项目不等于自动税务判断、报表审批或申报项目。

### 来源
1. [Maven官方FDE文章](https://www.mavenagi.com/resources/forward-deployed-engineers)
2. [K1x完整客户案例](https://www.mavenagi.com/customer-stories/k1x)
3. [K1x官方联系页](https://k1x.io/contact/)

## 10. Mastermind：活动高峰期网站、聊天与邮件客服

国家：美国；项目落地：未披露
行业：在线教育与创作者平台
国家口径：美国依据客户官方隐私页的Arizona联系地址及美国运营说明；不将其视作项目云托管或用户国家清单。实际AI部署国家未披露。

概述：用分渠道答复和人工辅助应对活动季客服波动。

流程：网站或聊天咨询→知识答复或转人工；邮件→AI生成草稿→客服处理。

落地程度：已投产；六周上线，案例报告上线后两个月内的结果。

人工职责：客服处理复杂问题与聊天升级，并使用邮件草稿和内部辅助；未证明邮件在该阶段全面自动发送。

证据说明：Maven联合创始人署名官方FDE文章的Customer Impact: Mastermind段，明确FDE与客户配置工作流并部署客服代理；完整项目案例提供交付和渠道细节。

可切入环节：分析：优先处理活动访问、账户使用等可验证问题；退款、订阅和账户变更单独授权。

- 聊天无需交接：93%。口径：2026年FDE文章口径；2025案例称live chat问题获答，不能外推到邮件渠道。

- 支持页面自主解决：68%。口径：独立于聊天渠道；未披露样本和重复联系率。

- 响应用时：减少75%。口径：案例同时报告联系量增加60%；未公开计时分位数和同质对照。

- 完整成本与净节省：未公开。口径：未增员并非现金成本减少；未披露软件费、实施、调用、维护或审核支出。

### 介入前的问题与基线

- 【公开披露】活动季咨询激增，按高峰全年配置坐席成本高，日常编制又难覆盖重复咨询。 [来源2](https://www.mavenagi.com/customer-stories/mastermind)

### 工程师具体做了什么

- 【公开披露】FDE与客户配置专属工作流并部署代理；官方后续文章确认聊天无需交接的比例。 [来源1](https://www.mavenagi.com/resources/forward-deployed-engineers)

- 【公开披露】交付团队与客服、QA、IT及留存负责人梳理流程、整理知识并连接邮件工具，六周投入运行。 [来源2](https://www.mavenagi.com/customer-stories/mastermind)

### 技术方案与数据流程

- 【公开披露】网站支持框和聊天控件面向用户；邮件Copilot基于知识起草答复，内部Copilot辅助坐席，仪表板展示表现及问题趋势。邮件工具品牌未公开。 [来源2](https://www.mavenagi.com/customer-stories/mastermind)

- 【分析／复现建议】复现建议：分别设置自助答复、坐席草稿与写入操作权限；每次模式切换保留审批记录。

- 【分析／复现建议】验收建议：以活动前后相同类型问题对照，区分首次响应、最终解决、返工和转人工等待；记录峰值并发。

### 解决程度与业务提升

- 【公开披露】上线后两个月内报告响应速度和支持页面自主解决改善；后续FDE文章另确认聊天交接表现。 [来源1](https://www.mavenagi.com/resources/forward-deployed-engineers) [来源2](https://www.mavenagi.com/customer-stories/mastermind)

### 尚未公开的信息

- 【未披露】基础模型名称、版本、模型提供商、微调或多模型路由未披露。ChatGPT式界面不是模型证据。

- 【未披露】托管云、区域、服务器资源、向量库和数据驻留未披露。

- 【未披露】邮件连接器、身份认证、提示结构、知识检索与同步实现、峰值容量未披露。

- 【未披露】FDE规模、完整经济性、质量评测集、独立审计及账户写入上线状态未披露。

### 关键技能
- 分析：多渠道工作流设计
- 分析：品牌知识与草稿质量管理
- 分析：季节性负载及客服排班评估

### 风险
- 分析：高峰期升级队列可能成为瓶颈，需测试异常流而非只测自动回答。
- 分析：账户和账单相关内容需防跨用户引用；草稿模式与自动发送须有独立权限。

### 限制
- 标题中的百万参会者属于活动规模，不等于百万AI用户或对话。
- 自动回复、退订和账户更改出现在后续扩展描述中，未作为本条已完成能力。
- 三个渠道的自动化和人工角色不同，不合并成一个总解决率。

### 来源
1. [Maven官方FDE文章](https://www.mavenagi.com/resources/forward-deployed-engineers)
2. [Mastermind完整客户案例](https://www.mavenagi.com/customer-stories/mastermind)
3. [Mastermind官方隐私页](https://learn.mastermind.com/privacy-session)

## 11. Hoxton Wealth：顾问客户报告生成与内部知识获取

国家：阿联酋／英国；项目落地：未披露
行业：财富管理与金融顾问服务
国家口径：主体所在地按2026-10-02行业报道的伦敦与迪拜双总部口径记录；客户官网另外确认CTO及产品、工程、设计、数据组织以迪拜为基地，并列有英国、阿联酋等分支。AWS项目未逐国披露实际使用团队、服务对象或云区域，因此deploymentCountries留空，不以总部或办公室清单推断部署。

概述：顾问报告耗时、知识依赖资深同事；Hoxton与AWS FDE共同改造相关内部工作流。

流程：AI辅助生成客户报告和演示、检索内部知识并支持合规检查；具体顺序与批准点未公开。

落地程度：2026-09-03合作已开展且CTO报告实际流程提速；同文仍称正在验证若干概念、希望上线，不能概括为所有功能已全面生产部署。

人工职责：顾问仍是报告与知识工具的使用者；公开材料未说明谁批准对客输出、如何复核合规检查或是否允许自动对外发送。

证据说明：AWS专属新闻稿直接确认Hoxton使用AWS FDE；客户CTO及AWS金融服务负责人分别作证。

可切入环节：分析：从单一内部报告草稿或只读知识问答开始；先固定资料范围、审核标准和基线，再扩大到合规检查辅助。

- 客户报告生成用时：数小时→数分钟。口径：2026-09-03客户CTO自报；样本、绝对时长及人工复核是否计入未公开。

- 合规检查用时：数天→原用时的一小部分。口径：客户自报的非精确描述；无可计算降幅，不代表正确率或监管认可。

- 生产部署覆盖：未公开。口径：项目已有实际流程效果陈述，但文中仍有概念验证和希望上线表述，未列功能逐项状态与覆盖人数。

- 总投入与净收益：未公开。口径：未披露实施、云资源、维护及人工复核成本，不能由节时推算净收益。

### 介入前的问题与基线

- 【公开披露】报告原需数小时，部分合规检查需数天；顾问答疑依赖少数资深同事。 [来源1](https://press.aboutamazon.com/aws/2026/9/hoxton-wealth-collaborates-with-aws-to-bring-agentic-ai-to-wealth-management)

### 工程师具体做了什么

- 【公开披露】AWS及合作伙伴与Hoxton共同验证AI报告和内部知识库；自主运营是交付目标，尚无能力移交验收披露。 [来源1](https://press.aboutamazon.com/aws/2026/9/hoxton-wealth-collaborates-with-aws-to-bring-agentic-ai-to-wealth-management)

### 技术方案与数据流程

- 【公开披露】公开实现细节限于AI生成报告及建设内部知识库；没有披露模型、AWS服务名、检索架构、CRM或文档系统接口。不能据AWS身份补写为Bedrock、AgentCore、RAG或知识图谱已被此项目采用。 [来源1](https://press.aboutamazon.com/aws/2026/9/hoxton-wealth-collaborates-with-aws-to-bring-agentic-ai-to-wealth-management)

- 【分析／复现建议】复现建议，非已披露实现：先将报告中的客户事实、数字和引用做结构化校验；保留原始材料、模板版本及逐项出处，任何对客发布都由具备权限的顾问复核。

- 【分析／复现建议】复现建议，非已披露实现：知识库应按司法辖区、业务实体、有效日期和资料权限隔离；无法确认规则适用范围或来源发生冲突时转交合规人员。

- 【分析／复现建议】复现建议，非已披露实现：分别评测报告事实准确率、知识检索支持率、合规检查漏报率与人工返工；将模型生成时长与包含人工审阅的端到端用时分开。

### 解决程度与业务提升

- 【公开披露】CTO自报报告与个性化演示可在数分钟内准备、信息获取加快及合规检查提速；无样本量或精确降幅，不能推出质量和净收益。 [来源1](https://press.aboutamazon.com/aws/2026/9/hoxton-wealth-collaborates-with-aws-to-bring-agentic-ai-to-wealth-management)

### 尚未公开的信息

- 【未披露】模型及版本、提示模板、数据源、分块和嵌入、检索索引、工具权限、CRM集成、缓存、审计日志及故障回滚未披露。

- 【未披露】实际生产与概念验证功能边界、上线日期、覆盖顾问数、使用频次、实际部署国家与云区域未披露。

- 【未披露】对客材料是否逐次强制人工审批、合规检查是否仅提供建议、数据处理及跨境传输控制未披露。

- 【未披露】FDE投入、实施与运行费用、人工复核成本、可复现评测、错误率、客户满意度和项目净收益未披露。

### 关键技能
- 分析：金融报告结构化校验与引用追溯
- 分析：多实体权限、辖区及知识版本管理
- 分析：端到端时间测量、质量评测与人工复核设计

### 风险
- 分析：客户资产及身份数据在报告生成、检索和跨实体调用中泄露。
- 分析：规则适用国家、版本或主体错配导致合规检查漏报。
- 分析：文字流畅但数值或来源不实的报告被直接用于对客建议。

### 限制
- FDE项目绑定强，但技术披露较薄；不把AWS通用参考架构当作客户实装。
- CTO同一份新闻稿同时描述现有提速和待验证、待上线概念；因此不标为全量正式生产。
- 公司AUM、App用户数和全球办公室数量不用于衡量本次FDE项目成效。
- 总部所在地依据最新行业报道；项目实际部署国家没有披露。

### 来源
1. [Hoxton Wealth Collaborates with AWS to Bring Agentic AI to Wealth Management](https://press.aboutamazon.com/aws/2026/9/hoxton-wealth-collaborates-with-aws-to-bring-agentic-ai-to-wealth-management)
2. [Hoxton Wealth：Mansel Oliver，Chief Technology Officer](https://hoxtonwealth.com/uk/team/mansel-oliver)
3. [Hoxton Wealth AUM tops US$5bn (£3.75bn)](https://www.international-adviser.com/hoxton-wealth-aum-tops-us5bn-3-75bn/)
4. [Hoxton Wealth：Contact / Our Global Presence](https://hoxtonwealth.com/ae/contact)

## 12. Sonos：音箱安装与连接故障排查代理

国家：美国；项目落地：未披露
行业：消费电子与音响
国家口径：Sonos官方联系页将总部列于美国加州Goleta；这只证明总部国家。项目案例未逐国披露实际部署用户或云区域，故部署国家留空。

概述：新用户安装音箱和排查路由器连接问题时，客服需跨手册与多个系统查找信息；Sierra将诊断、引导和工单接续做成对话代理。

流程：询问音箱型号及网络环境→收集基础诊断信息→跨系统取数并逐步引导设置→确认用户满意后在Salesforce建案；需要人工时附问题摘要转交。

落地程度：2024-07官方实施回顾明确已帮助真实用户设置Sonos音箱；初期覆盖首次购买后30天的服务旅程。

人工职责：客户技术团队参与需求范围与产品知识梳理；需人工支持的会话连同问题摘要升级。具体判断阈值及人工抽检比例未披露。

证据说明：直接参与者Natalie Meurer在Sierra官方文章中第一人称确认参与Sonos音箱连接排障代理。她在2026年会议演讲15:09–15:43回顾同一2024年角色定义，明确称Agent Engineering是FDE的一种。属于参与者回溯性角色认定并有官方项目佐证，不冒称当时职位原名为FDE。

可切入环节：分析：从单一音箱型号的安装排障开始，连接只读诊断和工单系统，明确转人工条件后再增加订单与退货事务。

- Time-to-music改善：未公开。口径：原文说明衡量目标，未给上线前后数值或对照组。

- 自动解决率与CSAT：未公开。口径：15 million是当时品牌客户规模，不能算AI使用量；未披露Sonos项目量化质量结果。

- 总投入与净收益：未公开。口径：未披露实施费、推理成本、人工复核成本或扣除成本后的节省。

### 介入前的问题与基线

- 【公开披露】早期服务聚焦购买后30天，既处理音箱设置，也排查路由器迁移、网络拓扑和IP地址；人工在系统、手册和程序之间切换。 [来源3](https://sierra.ai/customers/sonos)

- 【公开披露】客户希望缩短首次成功播放音乐所需的过程，并减少重复求助；Customer Effort Score综合联系频次、问题范围、产品使用和日志，而非仅看单次处理时长。 [来源3](https://sierra.ai/customers/sonos)

### 工程师具体做了什么

- 【公开披露】Meurer先与Sonos技术对口团队梳理产品组合和问题范围，再把连接排障步骤做成可重复执行的代理。其亲历叙述将人、客户和工作流直接绑定。 [来源1](https://sierra.ai/blog/meet-the-ai-agent-engineer)

- 【公开披露】从较简单的旅程扩展到新产品安装、路由器变更、订单退货及新音乐服务连接；2024年实施回顾确认Sonos设置流程已在真实用户中运行。 [来源3](https://sierra.ai/customers/sonos) [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

- 【公开披露】角色核验：2026年演讲回顾2024年Agent Engineer定义，称其是FDE的一种；这是后见性定义，非项目当年人事记录。 [来源2](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)

### 技术方案与数据流程

- 【公开披露】项目已披露的顺序是询问产品和环境、收集基础诊断、读取相关信息、指导设置，并在确认用户满意后写入Salesforce工单；人工接手收到问题摘要和相关信息。 [来源3](https://sierra.ai/customers/sonos)

- 【公开披露】技术背景，非Sonos逐项配置证明：Agent SDK以可组合技能表达流程，并约束系统记录调用的顺序；官方多客户实施文同时以Sonos排障和SiriusXM刷新说明多步骤集成复杂性。 [来源1](https://sierra.ai/blog/meet-the-ai-agent-engineer) [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

- 【公开披露】平台开发资料把代码、提示、模型依赖与知识库快照原子打包，支持回滚和A/B测试；这些是可用机制，未披露本项目的版本策略。 [来源5](https://sierra.ai/blog/agent-development-life-cycle)

- 【分析／复现建议】复现建议：将网络诊断读取与会改变用户设备状态的动作分开，要求用户确认危险步骤；对型号不明、已重复失败或信息矛盾的会话及时转人工。

- 【分析／复现建议】复现建议：验收覆盖新装、换路由器、音乐服务授权及失败重试，用成功播放、再次联系率、工单正确性共同评估，不只看对话是否结束。

### 解决程度与业务提升

- 【公开披露】官方材料证明安装、诊断和工单接续已成为可运行流程；客户负责人肯定多轮上下文能力。没有公开Time-to-music、Customer Effort Score或解决率的前后差值。 [来源3](https://sierra.ai/customers/sonos) [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

### 尚未公开的信息

- 【未披露】未披露底层模型、模型路由、检索分块与向量库、具体诊断API、身份鉴别或工具权限实现。

- 【未披露】未披露项目FDE投入人数、驻场方式、总工期、样本量、错误率、时延、成本或独立审计。

- 【未披露】实际用户部署国家、逐语言范围、2026年当前功能边界和版本变更未由这些历史案例确认。

### 关键技能
- 分析：设备与家庭网络排障建模
- 分析：诊断系统及Salesforce集成
- 分析：多轮对话状态、质量评测与安全转交

### 风险
- 分析：错误网络操作建议可能打断家庭网络或暴露设备信息。
- 分析：模型或知识版本改变后，原先正确的排障路径可能失效。

### 限制
- B级角色证据为2026年参与者对2024年Agent Engineer职责的回溯性认定；不能把她在Palantir的旧FDE职称当作Sonos证据。
- 通用Agent OS、Agent SDK与开发生命周期资料仅作技术背景；没有公开Sonos的具体模型、代码或配置。
- 15 million是品牌客户数，非代理触达数；客户对效率的正面描述不等于量化因果效果。

### 来源
1. [Meet the AI agent engineer](https://sierra.ai/blog/meet-the-ai-agent-engineer)
2. [The Dirty Secret of Forward Deployed Engineering：Natalie Meurer完整演讲与逐字稿](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)
3. [How Sonos elevates the listener experience with Sierra](https://sierra.ai/customers/sonos)
4. [Shipping and scaling AI agents](https://sierra.ai/blog/shipping-and-scaling-ai-agents)
5. [The Agent Development Life Cycle](https://sierra.ai/blog/agent-development-life-cycle)
6. [Contact Us | Sonos](https://www.sonos.com/en-ca/contact)

## 13. SiriusXM：Harmony车载收音机恢复与订阅客服

国家：美国；项目落地：未披露
行业：卫星广播与音频订阅
国家口径：2025年10-K列公司总部在纽约。项目背景描述美国与加拿大车载业务，但未分别披露Harmony部署和用户数据驻留地区，部署国家不据业务市场推断。

概述：旧机器人依赖关键词和固定路径，难理解口语意图，也难完成车载收音机刷新等多系统步骤；Harmony把理解和实际服务操作串成对话。

流程：订阅者用自然语言说明收音机或账户问题→识别具体意图并遵循业务步骤→调用系统发出卫星刷新信号或处理订阅服务→返回结果与内容指引。

落地程度：2024年已在生产中测试并运行；2025-12官方更新确认Harmony处理订阅、技术排障与内容推荐。ADP扩展当时仍待完整部署。

人工职责：客户Listener Care团队梳理政策及流程，并与Sierra共同定义需求。项目转人工条件、人工审批比例及对账方式未公开。

证据说明：Sierra工程负责人Natalie Meurer的2024官方文章明确将团队已设计并部署的SiriusXM卫星刷新工作流列为Agent Engineer实例；2026演讲15:09–15:43明确把该角色认定为FDE的一种。官方客户案例及2025更新验证Harmony实际服务。是团队负责人回溯性角色证言，未披露本项目具体工程师姓名。

可切入环节：分析：从低风险的频道查询和经身份核验的刷新请求开始，把付款及订阅变更置于单独授权与校验流程。

- 服务渠道体验排名：Harmony聊天为最高评分、最低费力渠道。口径：2025-12-04供应商自报，未给评分、样本、统计期间或可比性。

- 解决率及成本改善：未公开。口径：旧案例与更新没有给可复算的解决率、每次成本或前后对照。

- 总投入与净收益：未公开。口径：未披露实施、推理、支持和合规成本；不能由渠道排名推导财务收益。

### 介入前的问题与基线

- 【公开披露】原有团队花数月整理知识、用例及跨团队政策，再把规则写入传统机器人；预设路径难以处理非标准口语，也不能灵活完成复杂服务。 [来源3](https://sierra.ai/customers/siriusxm)

- 【公开披露】汽车收音机刷新需要业务专门知识和严格步骤，不能只用FAQ回答；客户希望保留自然语言灵活性，同时真正完成操作。 [来源3](https://sierra.ai/customers/siriusxm)

### 工程师具体做了什么

- 【公开披露】Meurer的官方实施文章把团队为SiriusXM设计部署卫星刷新代理列为明确实例；2026年她把2024年Agent Engineer角色回溯为FDE的一种。两项证据分别绑定项目和角色。 [来源1](https://sierra.ai/blog/meet-the-ai-agent-engineer) [来源2](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)

- 【公开披露】双方共同理解业务需求，建立Harmony并先在生产测试高频用例；后续官方回顾确认使用Agent OS组合技能及系统集成来发出刷新信号。 [来源3](https://sierra.ai/customers/siriusxm) [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

### 技术方案与数据流程

- 【公开披露】项目技术边界：Agent OS将多步骤任务和系统访问组合起来，实际触发卫星刷新；API名称、鉴权方式、设备匹配和重试机制未公开。 [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

- 【公开披露】平台背景：Agent SDK通过可组合技能表达业务流程并约束API顺序。2024年开发资料介绍用带mock API的会话模拟重放问题，形成发布前回归测试；没有公开Harmony测试集或通过门槛。 [来源1](https://sierra.ai/blog/meet-the-ai-agent-engineer) [来源6](https://sierra.ai/blog/agent-development-life-cycle)

- 【公开披露】ADP在2025-12被定位为Agent OS的记忆与上下文层；完整部署后才预期结合客户对话与业务结构化数据。不能从公告推定数据架构或生产上线日期。 [来源5](https://sierra.ai/blog/siriusxm-adp-announcement)

- 【分析／复现建议】复现建议：刷新请求应绑定已验证账户与唯一设备，执行后检查回执；将重试和重复用户请求做幂等处理，设备无法确认时升级人工。

- 【分析／复现建议】复现建议：对俗称频道、含糊故障描述、多个车载设备、付款失败和订阅取消分别设计验收，记录实际完成率而非只记录对话留存。

### 解决程度与业务提升

- 【公开披露】2025-12更新确认Harmony已处理订阅管理、技术排障与内容推荐，并可通过卫星信号刷新汽车收音机；文中称聊天体验在其服务渠道中评分最高、最省力，但没有披露原始量化数据。 [来源5](https://sierra.ai/blog/siriusxm-adp-announcement)

- 【公开披露】同一公告将ADP完全上线后的统一结构化与非结构化数据、跨旅程支持描述为预期，不计为已完成成效。 [来源5](https://sierra.ai/blog/siriusxm-adp-announcement)

### 尚未公开的信息

- 【未披露】基础模型、路由、检索方式、刷新API、付款渠道、权限与审计实现、人工接管规则未披露。

- 【未披露】FDE人数、驻场方式、项目总工期、延迟、每次成本、实际AI用户量和独立审计未公开。

- 【未披露】未核实ADP完整部署日期、跨会话记忆成效或2026年当前数据架构。

### 关键技能
- 分析：多步骤API编排与设备标识匹配
- 分析：订阅政策和口语意图建模
- 分析：业务回归测试与跨系统失败恢复

### 风险
- 分析：错配账户或设备可能把刷新信号发送到错误对象。
- 分析：订阅、账单和付款处理若缺少授权或幂等控制可能产生财务争议。
- 分析：跨会话记忆扩展会增加隐私、保留期限与访问隔离要求。

### 限制
- B级使用角色负责人2026年的回溯定义；非SiriusXM项目正式FDE职位名。
- 34 million是案例时点公司订阅者规模，不是Harmony用户数。
- 2025-12 ADP公告使用将来时，不能把长期记忆、统一客户数据或增长效益当作已实现结果。
- 平台模型和通用安全能力不等于Harmony具体配置。

### 来源
1. [Meet the AI agent engineer](https://sierra.ai/blog/meet-the-ai-agent-engineer)
2. [The Dirty Secret of Forward Deployed Engineering：Natalie Meurer完整演讲与逐字稿](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)
3. [How SiriusXM increases listener loyalty with Sierra](https://sierra.ai/customers/siriusxm)
4. [Shipping and scaling AI agents](https://sierra.ai/blog/shipping-and-scaling-ai-agents)
5. [SiriusXM and Sierra announce a deeper collaboration with the launch of Agent Data Platform](https://sierra.ai/blog/siriusxm-adp-announcement)
6. [The Agent Development Life Cycle](https://sierra.ai/blog/agent-development-life-cycle)
7. [Sirius XM Holdings 2025 Form 10-K](https://investor.siriusxm.com/sec-filings/all-sec-filings/content/0000908937-26-000006/siri-20251231.htm)

## 14. OluKai：鞋履选购与退换货服务代理

国家：美国；项目落地：未披露
行业：鞋履零售与电商
国家口径：OluKai官方帮助页明确总部在Irvine, California。夏威夷品牌风格不等于总部地点；美国和加拿大仓库也不能直接证明代理部署国家，故部署国家留空。

概述：电商增长使客服难维持响应速度，约四分之三请求为订单和退货等常见问题；项目把选购引导、政策解释及退换货操作接入全天候代理。

流程：消费者描述穿鞋场景或订单问题→代理结合产品信息和服务政策回应→退货场景介绍Happy Returns并提供附近地点→处理可覆盖请求，复杂情形留给Day Makers人工客服。

落地程度：2024-07工程文章确认已部署鞋履选择工作流；同期实施回顾确认代理在处理OluKai退换货。客户案例披露上线后的客服解决率。

人工职责：Aloha Experience团队逐会话看评分和仪表板；代理承担常见问题后，人工Day Makers专注复杂、需情感理解的情况。明确例外审批层级未公开。

证据说明：Natalie Meurer的2024官方文章把团队设计并部署的OluKai场景选鞋工作流列为Agent Engineer实例；其2026会议演讲将该角色回溯定义为FDE的一种。官方实施回顾与客户案例另证同一品牌代理的退换货使用。指标属于整体客服代理，不能归因给单独导购旅程。

可切入环节：分析：先覆盖订单状态与标准退货，建立可审计例外规则，再开放场景化推荐与更复杂的个性化服务。

- 无人工介入解决率：约70%。口径：官方客户案例自报整体客服代理票单/询问解决率；不等于导购转化率，观察期和样本量未知。

- 会话满意度：约4.5/5。口径：按会话评分监测；4.75为目标而非已实现结果，缺乏独立验证。

- 人工首响基线：2–48小时。口径：取决于业务繁忙程度；AI被描述为即时响应，但未披露可复算延迟或完整处理时长。

- 总投入与净收益：未公开。口径：未公开完整实施及运营成本；不能将退货更方便等同于已量化的利润改善。

### 介入前的问题与基线

- 【公开披露】业务增长增加电话、邮件和社媒咨询，约75%是常见订单或退货问题；旧机器人因速度和效果不足被撤下，人工响应通常需2–48小时。 [来源3](https://sierra.ai/customers/olukai)

### 工程师具体做了什么

- 【公开披露】团队将品牌知识、服务政策及语气用于代理；Meurer单独确认Agent Engineers已设计部署OluKai场景选鞋，另一官方实施回顾确认正在处理退换货。 [来源1](https://sierra.ai/blog/meet-the-ai-agent-engineer) [来源3](https://sierra.ai/customers/olukai) [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents)

- 【公开披露】角色证据来自同一工程负责人2026年的回溯定义，不能据其其他雇主旧职位或行业通用职责推定。 [来源2](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)

### 技术方案与数据流程

- 【公开披露】具名工作流包含解释Happy Returns并给出附近网点，以及在30天退货政策周围按情境作例外；未公开所调用的退货、订单或定位API。 [来源3](https://sierra.ai/customers/olukai)

- 【公开披露】项目技术证据还包括真实退货与换货任务；平台背景是Agent OS的组合技能，通用发布机制支持冻结提示、模型和知识版本。不能据平台材料断言OluKai具体规则配置。 [来源4](https://sierra.ai/blog/shipping-and-scaling-ai-agents) [来源5](https://sierra.ai/blog/agent-development-life-cycle)

- 【公开披露】客户已按会话收集评分并通过绩效仪表板监测；通用生命周期文介绍把人工标注问题转为mock API回归测试，未公开OluKai是否及如何采用该完整流程。 [来源3](https://sierra.ai/customers/olukai) [来源5](https://sierra.ai/blog/agent-development-life-cycle)

- 【分析／复现建议】复现建议：把标准退货资格、允许例外范围及需要人工审批的条件写成独立规则；用户确认后再调用退货工具，确保重复请求不重复退款。

- 【分析／复现建议】复现建议：分开评估导购、订单查询与退货，分别量化推荐适合度、事务成功率、重复联系和满意度，避免总解决率掩盖某旅程失败。

### 解决程度与业务提升

- 【公开披露】客户案例自报整体客服约70%请求无人工介入解决，会话评分约4.5/5；人工每日150张票单的旧目标随后降低，以留出时间处理复杂问题。样本和观察窗口未公开。 [来源3](https://sierra.ai/customers/olukai)

- 【公开披露】4.75评分是目标；CDP驱动个性化、延迟配送主动消息及带动购买等仍属探索方向，不是已实现增收。 [来源3](https://sierra.ai/customers/olukai)

### 尚未公开的信息

- 【未披露】底层模型、产品检索索引、工具接口、付款或退款权限、例外授权实现、人工升级规则未披露。

- 【未披露】工程投入、上线工期、评分样本和时间窗口、对照组、推理成本及净利润影响未公开。

- 【未披露】用户国家、数据驻留、导购转化率、CDP后续上线情况和2026年当前架构未由本次材料确认。

### 关键技能
- 分析：零售政策及例外建模
- 分析：退货地点与订单工具集成
- 分析：客服质量评估与人工升级

### 风险
- 分析：把弹性退货政策交给不受约束生成可能产生不一致待遇或损失。
- 分析：推荐产品或附近退货点若数据过期会误导消费者。

### 限制
- 角色认定为B级回溯证据；Meurer陈述的是团队项目，未公开OluKai具体工程师姓名。
- 工程角色原文绑定场景选鞋，退换货由同期具名实施回顾补证；70%和4.5/5仅属于整体支持代理，不能当作单独选购流程指标。
- 4.75满意度、客户数据平台个性化、主动提醒与收入增长是目标或探索，未计入已实现。
- 不把另篇匿名零售客户45天例外硬套到OluKai；其具名案例仅举迟5–6天的30天政策例外。

### 来源
1. [Meet the AI agent engineer](https://sierra.ai/blog/meet-the-ai-agent-engineer)
2. [The Dirty Secret of Forward Deployed Engineering：Natalie Meurer完整演讲与逐字稿](https://ai.engineer/talks/Byv311hdoHE-dirty-secret-forward-deployed-engineering)
3. [How OluKai scales the Aloha experience with Sierra](https://sierra.ai/customers/olukai)
4. [Shipping and scaling AI agents](https://sierra.ai/blog/shipping-and-scaling-ai-agents)
5. [The Agent Development Life Cycle](https://sierra.ai/blog/agent-development-life-cycle)
6. [OluKai Help：What’s your address?](https://support.olukai.com/en-US/whats-your-address-1121446)

## 15. LSEG（伦敦证券交易所集团）：Workspace AI Search：有引用的金融信息检索

国家：英国；项目落地：未披露
行业：金融数据与分析
国家口径：英国为集团注册所在地：Companies House列注册地址为伦敦。项目没有逐国披露用户分布或云区域；产品可用地区不能代替实际部署国家。

概述：金融专业人员原先需跨工具查找信息并阅读大量材料；项目将检索和分析接回Workspace。

流程：自然语言问题→检索获授权金融数据与文档→带来源的回答、表格或图表→用户核验并继续追问或导出。

落地程度：2026-06-23首次正式发布；10月FAQ列Workspace、Teams和Microsoft 365 Copilot入口。

人工职责：用户核验关键数据；具体机构是否要求逐条人工审批未披露。

证据说明：微软官网由LSEG AI工程负责人明确确认：LSEG与Microsoft FDE共同开发Workspace AI Search；项目与角色直接绑定。

可切入环节：分析：从一种已授权资料的只读检索做起，保留逐项引用和人工核验，再接入结构化分析。

- 活跃用户：17,000。口径：LSEG于2026-07-30自报；活跃周期和去重口径未披露，非付费机构数。

- 任务效率变化：未公开。口径：发布说明和业绩更新未给出可比前后用时或生产率测量。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】原有工作需要在不同工具、数据和长文档之间人工串联信息；7月介绍将市场数据、公司披露、新闻与金融分析放在同一交互中。 [来源2](https://www.lseg.com/en/data-analytics/products/workspace/updates/act-with-the-same-confidence-at-a-new-speed-introducing-lseg-workspace-ai-search)

### 工程师具体做了什么

- 【公开披露】LSEG技术负责人明确披露共同工程采用RAG、MCP与前沿大模型。没有公开双方各自提交的代码、团队人数或驻场时长。 [来源1](https://www.microsoft.com/en-us/frontier-company)

### 技术方案与数据流程

- 【公开披露】10月FAQ列GPT-5及以上、Claude Opus 4.6及以上，在LSEG的安全Azure基础设施中用于RAG与编排；精确模型快照和路由规则未知。 [来源3](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/lseg-workspace-ai-search-faq.pdf)

- 【公开披露】按个人数据授权检索；AMR先语义召回，再选原文片段独立展示，不生成摘要，也不混入其他来源生成答案。 [来源3](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/lseg-workspace-ai-search-faq.pdf)

- 【公开披露】内容与滥用检测组合确定性及LLM过滤；提示和回答不训练基础模型，可匿名用于产品评估。 [来源3](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/lseg-workspace-ai-search-faq.pdf)

- 【公开披露】6月发布说明已列引用追溯、反馈、图表与导出，同时记录过缺失引用、显示及授权一致性问题；不能据旧版问题单断言10月仍未修复。 [来源4](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/ai-search-release-notes.pdf)

- 【分析／复现建议】复现建议：把权限检查放在检索前后，分别测试结构化数值引用与文档引用；对无数据、过期数据和冲突口径允许拒答，不以语言流畅度代替准确率。

- 【分析／复现建议】复现建议：为各授权内容类型建立独立输出规则，将AMR原文提取与可生成总结的材料分开；上线验收同时衡量引用支持率、数值一致性及越权召回。

### 解决程度与业务提升

- 【公开披露】2026年6月23日首次正式发布；7月30日中期业绩更新报告17,000名活跃用户。未披露活跃周期、付费转化或任务节省时间。 [来源4](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/ai-search-release-notes.pdf) [来源5](https://www.lseg.com/en/investor-relations/financial-results/2026-h1-interim-results)

### 尚未公开的信息

- 【未披露】检索索引、分块/嵌入、MCP工具清单、调用权限实现、缓存与故障切换未公开。

- 【未披露】未公开可复现评测集、引用错误率、幻觉率、端到端延迟、每问成本和独立审计结果。

- 【未披露】未公开FDE投入、项目整体工期、订阅增收、净收益及用户所在国家。

### 关键技能
- 分析：金融数据授权与检索
- 分析：MCP编排及逐项引用验证
- 分析：分内容类型评测

### 风险
- 分析：授权内容泄露、过时行情和数值引用错配。
- 分析：把信息检索误用为投资建议或自动交易依据。

### 限制
- 10月FAQ明确中国大陆用户不可用，实时行情不支持；7月文章中的Copilot即将推出已由10月入口说明更新。
- AMR初期在Copilot不可用；不能概括为所有来源、所有入口都能生成摘要。
- 2025版Explainability Note仍列Beta旧模型，不用于推断2026生产模型。
- 本案例是信息辅助；不将活跃用户量解释成研究正确率、交易收益或工作时长改善。

### 来源
1. [Microsoft Frontier Company：LSEG项目负责人证言](https://www.microsoft.com/en-us/frontier-company)
2. [Introducing LSEG Workspace AI Search](https://www.lseg.com/en/data-analytics/products/workspace/updates/act-with-the-same-confidence-at-a-new-speed-introducing-lseg-workspace-ai-search)
3. [LSEG Workspace AI Search FAQ，版本2610.01](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/lseg-workspace-ai-search-faq.pdf)
4. [AI Search Release Notes，版本2606.01](https://www.lseg.com/content/dam/data-analytics/en_us/documents/support/workspace/ai-search-release-notes.pdf)
5. [LSEG 2026 H1 Interim Results](https://www.lseg.com/en/investor-relations/financial-results/2026-h1-interim-results)
6. [Companies House：LONDON STOCK EXCHANGE GROUP PLC](https://find-and-update.company-information.service.gov.uk/company/05369106)

## 16. Core42：Sovereign Public Cloud：主权云控制与持续监测

国家：阿拉伯联合酋长国；项目落地：阿拉伯联合酋长国
行业：云基础设施与安全治理
国家口径：Core42官方新闻明确总部在阿联酋；本项目另由产品页明确Azure阿联酋区域基础设施与数据驻留，因此部署国家有项目级依据。其他海外业务不计入。

概述：面向阿联酋公共部门及受监管机构，需要将云服务与数据主权、安全及持续监控要求结合。

流程：云资源纳入主权控制→Insight显示资产、策略状态及漂移→给出整改建议→运维与合规人员处理。

落地程度：已提供产品且有Aldar采用故事；未公开FDE共建工期及全部客户部署规模。

人工职责：安全与合规团队使用监测和建议；自动修复的授权边界、强制审批及人工处理比例未披露。

证据说明：微软官网由Core42首席商务官直接确认FDE与团队协作并参与定义Sovereign Public Cloud背后的IP；客户产品资料说明具体能力。

可切入环节：分析：先针对一类资源验证一组关键主权控制，以只读监测和人工整改建立可信基线。

- 控制库规模：200+项。口径：产品映射的技术控制数量，属于功能覆盖；不是已避免的违规事件或风险降幅。

- 治理与运维效率：未公开。口径：没有同口径前后审计人时、误报率、修复用时或迁移速度。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】Core42将问题描述为从阶段性审计转向持续掌握主权、安全与加密控制状态；传统可见性不足的论述是供应商背景说明，未给本项目实施前基线。 [来源3](https://www.core42.ai/resource/blogs/core42-insight-makes-data-sovereignty-measurable)

### 工程师具体做了什么

- 【公开披露】客户高管明确将Microsoft FDE协作绑定到Sovereign Public Cloud的IP定义。没有披露FDE是否独立实现Insight的每一个模块。 [来源1](https://www.microsoft.com/en-us/frontier-company)

### 技术方案与数据流程

- 【公开披露】产品组合Azure区域基础设施与Insight SaaS；官方声明数据驻留阿联酋，配有主权landing zone、预设guardrail和部署模板。 [来源2](https://www.core42.ai/products/sovereign-public-cloud)

- 【公开披露】Insight映射200多项技术控制，显示资源区域、30天趋势及不合规标记，并提供上下文相关建议。数字是功能范围，非风险降低效果。 [来源2](https://www.core42.ai/products/sovereign-public-cloud)

- 【公开披露】Insight介绍进一步披露加权合规评分、严重度排序与Insight Assist整改指导；未给评分权重、准确率或自主执行整改的权限机制。 [来源3](https://www.core42.ai/resource/blogs/core42-insight-makes-data-sovereignty-measurable)

- 【分析／复现建议】复现建议：从一组资源和一套控制开始，把政策要求映射到可机器检查的配置，保存证据时间戳与版本；地区驻留、密钥控制和操作权限分别验证。

- 【分析／复现建议】复现建议：建议与执行分离；用误报、漏报、修复用时和审计取证人时验收，关键变更由授权运维确认并可回滚。

### 解决程度与业务提升

- 【公开披露】Aldar官方客户故事确认已采用该产品并使用Insight掌握安全及加密控制，支持产品已被使用；没有证明微软FDE直接参与Aldar部署。 [来源4](https://www.core42.ai/resource/blogs/aldars-blueprint-for-secure-digital-transformation)

- 【未披露】未披露本共建项目减少的违规事件、审计人时、迁移用时或运营成本。

### 尚未公开的信息

- 【未披露】具体策略规则、扫描频率、评分公式、密钥托管方式、隔离与访问控制实现未公开。

- 【未披露】模型供应商与版本、建议生成链路、评测数据和人工审批制度未公开；不能补画为全自动整改代理。

- 【未披露】FDE人数、投入工期、产品客户总数、资源覆盖量与项目完整成本未公开。

- 【未披露】本次资料未给可核验的独立合规认证或审计结论；产品的合规主张不等于逐一法律要求均已被认证满足。

### 关键技能
- 分析：云治理与政策即代码
- 分析：主权边界和密钥管理验证
- 分析：审计证据及整改闭环

### 风险
- 分析：控制映射或扫描遗漏可能造成错误安全感。
- 分析：跨区域操作、数据分类错误及过度自动修复。

### 限制
- 适用Open与Confidential/Sensitive级别；Secret和Top Secret被导向另一私有云产品，不混入本案例。
- 200+控制和30天趋势为功能说明；产品合规声明不作为独立认证或效果审计。
- 本记录主体为Core42共建产品；Aldar只作实际采用佐证，不另计一个FDE客户项目。
- Insight介绍中的多云通用能力不等于本Azure主权公有云已逐项交付所有跨云实现。

### 来源
1. [Microsoft Frontier Company：Core42项目证言](https://www.microsoft.com/en-us/frontier-company)
2. [Core42 Sovereign Public Cloud](https://www.core42.ai/products/sovereign-public-cloud)
3. [Core42 Insight Makes Data Sovereignty Measurable](https://www.core42.ai/resource/blogs/core42-insight-makes-data-sovereignty-measurable)
4. [Aldar’s Blueprint for Secure Digital Transformation](https://www.core42.ai/resource/blogs/aldars-blueprint-for-secure-digital-transformation)
5. [Core42 Raises USD 550 million from HSBC to Scale Global AI Infrastructure](https://www.core42.ai/resources/news/core42-raises-usd-550-million-from-hsbc-to-scale-global-ai-infrastructure)

## 17. JPMorganChase（摩根大通）：CCB Risk数据与notebook迁移

国家：美国；项目落地：未披露
行业：银行与风险数据工程
国家口径：美国为集团总部国家：JPMorganChase官方纽约页面明确全球总部在纽约。本CCB Risk迁移没有披露云区域或实际部署国家。

概述：CCB Risk需要完成大规模数据及notebook迁移，并让平台用户具备使用能力。

流程：迁移风险数据与notebook，并开展平台培训；详细迁移顺序、切换及验收流程未披露。

落地程度：2026-06-11客户证言报告迁移已完成并继续合作；没有公开全行迁移完成或后续AI应用上线。

人工职责：Databricks FDE承担工程交付与培训；银行用户参加培训。具体银行验收、风险审批和运维职责未公开。

证据说明：Databricks官方FDE发布文章刊载JPMC消费与社区银行CTO Bala Vadhiyar的具名证言，直接说明FDE完成CCB Risk迁移。角色与项目明确，但实施技术披露不足。

可切入环节：分析：从一个可独立对账的风险数据域开始，先明确验收和回滚条件，再扩大迁移范围。

- 迁移数据量：5+ PB。口径：客户CTO报告的CCB Risk迁移范围，非处理吞吐率。

- 迁移notebook数：500+。口径：未披露语言、复杂度或作业覆盖率。

- 交付时长：4个月。口径：完成上述迁移的报告工期；无原计划或对照，不能计算提速倍数。

- 培训用户：600+。口径：培训覆盖，非平台活跃用户或已通过考核人数。

- 迁移后效率变化：未公开。口径：没有可比查询时延、运行成本或迁移提速基线。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】公开材料将交付对象限定为CCB Risk数据和notebook；没有描述原平台、旧系统瓶颈或迁移前性能。 [来源1](https://www.databricks.com/blog/forward-deployed-engineering-delivering-business-outcomes-ai)

### 工程师具体做了什么

- 【公开披露】客户CTO把工程迁移与用户培训直接归于Databricks FDE团队，并表示后续合作持续。 [来源1](https://www.databricks.com/blog/forward-deployed-engineering-delivering-business-outcomes-ai)

### 技术方案与数据流程

- 【公开披露】已知技术交付物只有数据迁移与notebook迁移，不能由这段证言还原数据格式、代码转换、调度或生产切换架构。 [来源1](https://www.databricks.com/blog/forward-deployed-engineering-delivering-business-outcomes-ai)

- 【未披露】未找到项目专属技术论文、架构图或迁移运行手册；Databricks通用Lakehouse、Lakebridge和KARL资料不能作为本项目采用证据。

- 【分析／复现建议】复现建议，非本项目已披露做法：先盘点数据与notebook依赖，按业务重要性分批迁移；为记录数量、关键风险汇总及权限建立新旧对账，再由负责人决定切换。

- 【分析／复现建议】复现建议：分别记录迁移完成、作业正确运行和用户独立操作三个验收状态，保留回滚方案；培训人数不能代替平台实际活跃度或风险模型正确性。

### 解决程度与业务提升

- 【公开披露】客户证言报告：四个月内迁移5 PB以上数据及500多个notebook，并培训600多名用户；没有给出对照工期、误差率或财务回报。 [来源1](https://www.databricks.com/blog/forward-deployed-engineering-delivering-business-outcomes-ai)

### 尚未公开的信息

- 【未披露】源系统、目标云区域、存储格式、分区与增量同步方案均未披露。

- 【未披露】notebook语言、自动转换工具、代码修改量及调度依赖处理未披露。

- 【未披露】双跑或停机安排、数据对账规则、权限迁移、回滚条件及银行验收流程未披露。

- 【未披露】迁移后查询性能、风险指标一致性、失败率、600多名受训者后续活跃度与生产覆盖量未披露。

- 【未披露】FDE团队人数、确切起止日期、资源投入、费用与净收益未披露。

### 关键技能
- 分析：数据依赖盘点与对账
- 分析：notebook兼容性和调度验证
- 分析：银行验收及用户培训

### 风险
- 分析：迁移可能影响数据一致性、作业依赖与访问权限；本项目错误率未知。
- 分析：把培训量当成熟度或将迁移完成当全行转型完成。

### 限制
- 技术细节不足：本条确认的是具名FDE工程交付、迁移范围和培训结果；字段齐全不代表已获得完整实现。
- 仅保留5+ PB、500+ notebooks、4个月、600+用户四项已报事实；不估算ROI或归因全行AI收益。
- 不能把邻近的Databricks通用产品说明、其他银行项目或招聘技术栈移植为CCB Risk实际架构。

### 来源
1. [Forward Deployed Engineering: Delivering Business Outcomes with AI](https://www.databricks.com/blog/forward-deployed-engineering-delivering-business-outcomes-ai)
2. [Our Impact in New York City](https://www.jpmorganchase.com/communities/new-york)

## 18. Kantar：LINK AI广告评估与优化平台

国家：英国；项目落地：未披露
行业：广告与市场研究
国家口径：微软官方案例的客户国家字段为英国；未披露部署国家或云区域。

概述：广告评估与创意修改脱节，批量评分和生成需求增大。

流程：评分→建议→受控生成变体→重新评分，由人决定发布。

落地程度：已上线；规模未公开

人工职责：创意团队保留最终发布权。

证据说明：官方案例明确Microsoft FDE共同改造LINK AI，并由客户架构负责人确认。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 批量评分速度：20倍。口径：平台改造前后；不是广告投资回报。

- 平台运行费用：约降至1/4。口径：官方“reduced ... by 4x”口径；不含完整实施成本。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】原LINK AI主要预测广告效果，客户还需把低分反馈转成修改方案。 [来源1](https://www.microsoft.com/en/customers/story/27379-kantar-azure)

### 工程师具体做了什么

- 【公开披露】FDE参与LINK AI架构重构及团队采用新架构的过程。 [来源1](https://www.microsoft.com/en/customers/story/27379-kantar-azure)

### 技术方案与数据流程

- 【公开披露】Foundry编排与治理，Azure OpenAI负责生成和推理；AKS运行20多个模型，Service Bus连接工作流，Cosmos DB与PostgreSQL保存元数据及创意表现。 [来源1](https://www.microsoft.com/en/customers/story/27379-kantar-azure)

- 【分析／复现建议】复现建议：先冻结评分模型和测试广告集，再比较生成前后分数，防止生成器只迎合评分器；保存版本、提示、素材授权及审批记录。

- 【分析／复现建议】复现建议：将吞吐量、单视频延迟和总平台开销分开压测；对排队、失败重试和高峰资源单独计量。

### 解决程度与业务提升

- 【公开披露】官方报告批量评分20倍、单视频评分6倍加速及平台运行费用降至约四分之一；已累计评分逾10万条视频广告。 [来源1](https://www.microsoft.com/en/customers/story/27379-kantar-azure)

### 尚未公开的信息

- 【未披露】基线硬件、样本分布、绝对延迟及各成本分项未披露；未报告可归因广告收入增量。

### 关键技能
- 分析：异步编排与弹性算力
- 分析：生成内容评测及人工审批

### 风险
- 分析：生成内容知识产权、品牌安全与评分器偏差。

### 限制
- 实时在投广告优化是后续待验证方向。

### 来源
1. [Kantar turns advertising intelligence into action with Microsoft AI](https://www.microsoft.com/en/customers/story/27379-kantar-azure)

## 19. Kawasaki Heavy Industries（川崎重工）：机器人即服务平台基础

国家：日本；项目落地：未披露
行业：机器人与工业制造
国家口径：微软案例客户国家字段为日本；未公开具体医疗部署机构或国家。圣何塞研发中心不能代替部署证据。

概述：每个机器人项目重复开发和集成，难以复用软件。

流程：容器化机器人能力、集中管理遥测与状态，结合自然语言操作和数字孪生验证。

落地程度：共同构建的平台基础已形成；RaaS持续开发，非全行业规模部署完成。

人工职责：工程师验证应用；医疗工作人员使用辅助工具。

证据说明：川崎管理人员在官方案例中明确称与Microsoft Forward Deployed Engineering共同构建平台基础。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 平台效率变化：未公开。口径：无可直接绑定本次FDE平台的基线、部署量或效率评测。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】软件、集成及流程与单个机器人部署紧耦合。 [来源1](https://www.microsoft.com/en/customers/story/26946-kawasaki-heavy-industries-azure-kubernetes-service)

### 工程师具体做了什么

- 【公开披露】FDE共同交付面向医疗机器人的平台基础；整体RaaS仍在开发。 [来源1](https://www.microsoft.com/en/customers/story/26946-kawasaki-heavy-industries-azure-kubernetes-service)

### 技术方案与数据流程

- 【公开披露】AKS复用容器化应用；Cosmos DB管理遥测和状态，Azure OpenAI支持自然语言，IoT Operations连接设备，Digital Twins用于仿真、监测和投产前验证。 [来源1](https://www.microsoft.com/en/customers/story/26946-kawasaki-heavy-industries-azure-kubernetes-service)

- 【分析／复现建议】复现建议：自然语言到机器人动作之间加入确定性授权与安全约束，异常时停机或转人工；云端推理不得绕过设备原有保护。

- 【分析／复现建议】复现建议：用仿真和有限场景验收，再逐步扩大设备范围；记录指令、模型版本、动作和传感器结果以支持回放与回滚。

### 解决程度与业务提升

- 【公开披露】形成可跨设备复用的应用与运维基础；官方未给出平台覆盖机器人数量。 [来源1](https://www.microsoft.com/en/customers/story/26946-kawasaki-heavy-industries-azure-kubernetes-service)

### 尚未公开的信息

- 【未披露】硬实时控制架构、断网策略、安全测试指标、设备覆盖量及平台净收益未公开。

### 关键技能
- 分析：边云协同与设备接口
- 分析：仿真验收与安全约束

### 风险
- 分析：物理动作风险、网络中断和错误指令。

### 限制
- 报道中某医疗实例的护士日行走20→10公里未充分绑定本次FDE平台，故不作为项目绩效。

### 来源
1. [Kawasaki builds scalable robotics as a service platform with Azure Kubernetes Service](https://www.microsoft.com/en/customers/story/26946-kawasaki-heavy-industries-azure-kubernetes-service)

## 20. Order.co：数据仓库与Metabase迁移

国家：美国；项目落地：未披露
行业：采购与支付软件
国家口径：官方案例客户地点为纽约，美国；未披露云部署区域或使用者所在国家。

概述：开发、生产、临时分析与实时请求争用Redshift资源。

流程：六波迁移数据层、仪表板及推理管线，并行对照验证后切换。

落地程度：已上线；规模未公开

人工职责：工程师调整迁移自动化并检查一致性。

证据说明：官方案例明确FDE共同迁移并开发定制迁移skills，客户直接确认。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 分析查询速度：2—7倍。口径：客户报告；不同查询表现不同。

- 迁移范围：约5TB、近9000份报表。口径：两个月左右；一位工程师仅指仪表板迁移子任务。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】资源争用影响生产，且大JSON对象导致维护两套平台。 [来源1](https://www.snowflake.com/en/customers/all-customers/case-study/order-co/)

### 工程师具体做了什么

- 【公开披露】FDE建立网络策略、资源监控和治理基线，并提供迁移工具。 [来源1](https://www.snowflake.com/en/customers/all-customers/case-study/order-co/)

### 技术方案与数据流程

- 【公开披露】先搬迁再优化：bronze/silver到gold、仪表板、ML推理与reverse ETL共六波；AIM、CoCo及FDE定制skills转换dbt和仪表板，对比新旧结果。 [来源1](https://www.snowflake.com/en/customers/all-customers/case-study/order-co/)

- 【分析／复现建议】复现建议：每波建立行数、金额汇总、空值及关键业务查询对账；双跑期间固定时间窗口，区分迟到数据与迁移错误。

- 【分析／复现建议】复现建议：保留源平台和回切点；将仪表板负责人签字、权限迁移、成本预算作为切换门槛。

### 解决程度与业务提升

- 【公开披露】约两个月迁移5TB并支持200多位Metabase用户；近9000份仪表板/报表迁移由一位工程师完成该子任务，查询加速2—7倍。 [来源1](https://www.snowflake.com/en/customers/all-customers/case-study/order-co/)

### 尚未公开的信息

- 【未披露】各查询基线、全项目团队人数、失败率与迁移费未公开。

### 关键技能
- 分析：分批迁移与对账
- 分析：AI辅助代码转换

### 风险
- 分析：语义偏差和权限迁移遗漏。

### 限制
- CoWork和Cortex Agents的对话分析仍在路线图上，不计作已交付。

### 来源
1. [Order.co Takes the Pain Out of Procurement with up to 7x Faster Analytics](https://www.snowflake.com/en/customers/all-customers/case-study/order-co/)

## 21. Snowflake（内部审计团队）：收入相关合同审核代理

国家：美国；项目落地：未披露
行业：企业软件与内部审计
国家口径：本条客户为Snowflake内部团队；美国为公司归属口径，实际处理或部署国家未公开。

概述：人工逐份阅读订单、主协议和修订，审计只能覆盖样本。

流程：提取条款→规则分类及新颖条款检测→审计师批准、纠正或升级。

落地程度：已上线；规模未公开

人工职责：审计师定义规则、处理例外并保留判断。

证据说明：官方首段明确是FDE团队建设且已内部使用的真实案例，不是示例架构。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 审核时间：减少70%。口径：内部团队报告；不是总会计成本或错误减少70%。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】每季度数千份订单条款需要检查收入确认影响，人工逐页阅读限制覆盖。 [来源1](https://www.snowflake.com/en/blog/agentic-intelligence-contract-review-snowflake/)

### 工程师具体做了什么

- 【公开披露】FDE建设审计副驾驶，自动检测但由审计人员决策。 [来源1](https://www.snowflake.com/en/blog/agentic-intelligence-contract-review-snowflake/)

### 技术方案与数据流程

- 【公开披露】Google Drive经Openflow入库；Cortex Agent与AI Extract提取字段，匹配审计团队维护的规则表，给出置信度、原文、页码和解释。语义偏离标准条款的文本进入新颖性复核；规则变化和纠正保留审计轨迹。 [来源1](https://www.snowflake.com/en/blog/agentic-intelligence-contract-review-snowflake/)

- 【分析／复现建议】复现建议：按合同家族而非随机页面划分评测，评估漏检非标准条款率；低置信度必须人工审阅，不能将相似措辞当法律等价。

- 【分析／复现建议】复现建议：将规则、字段提取器和合同版本绑定；纠正反馈先审查再进入后续上下文，避免误标逐次放大。

### 解决程度与业务提升

- 【公开披露】报告审核耗时减少70%，从天级转为小时级，扩大季度合同覆盖。 [来源1](https://www.snowflake.com/en/blog/agentic-intelligence-contract-review-snowflake/)

### 尚未公开的信息

- 【未披露】未公开召回率、误报率、基线样本及外部审计独立验证。

### 关键技能
- 分析：文档提取与溯源
- 分析：规则治理与专家反馈

### 风险
- 分析：漏检条款及规则错误影响审计判断。

### 限制
- 文章界面配图是AI生成示意，不是客户真实数据。
- 长期保存纠正提示不等于已公开模型微调。

### 来源
1. [How Snowflake Reduced Contract Review Time by 70% with Agentic Intelligence](https://www.snowflake.com/en/blog/agentic-intelligence-contract-review-snowflake/)
2. [Snowflake Privacy Notice](https://www.snowflake.com/en/legal/privacy/privacy-policy/)

## 22. Hays：多语言候选人与岗位匹配

国家：英国；项目落地：澳大利亚、新西兰
行业：招聘服务
国家口径：Hays官方集团联系地址为伦敦；联讲明确alpha测试版已在澳大利亚、新西兰发布，不能外推全球全面上线。

概述：多语言简历难统一，原搜索约20秒；专业岗位重精度、高量岗位重速度。

流程：技能规范化及分块→关键词与向量检索→融合排序→招聘顾问审阅。

落地程度：澳新alpha测试版已发布；全球推广未证实。

人工职责：顾问评估结果、调整权重和审查未知技能。

证据说明：Hays代表00:24明确与FDE合作，12:10明确该alpha由双方共同构建；FDE负责人共同讲解实现。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 搜索延迟：约20秒→低于3秒。口径：早期alpha结果；低于500毫秒是目标。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】简历语言、技能别名和信息缺失妨碍搜索，原始延迟约20秒。 [来源1](https://answers.databricks.com/hays-databricks-build-ai-candidate-job-matching-engine-x_dYacZctsI)

### 工程师具体做了什么

- 【公开披露】双方从既有原型迭代，限定首批人群，招聘分析人员共同设计评测。 [来源1](https://answers.databricks.com/hays-databricks-build-ai-candidate-job-matching-engine-x_dYacZctsI)

### 技术方案与数据流程

- 【公开披露】ESCO锚定多语言技能；按技能、经历、资格等分块。别名、字典、模糊及向量匹配后，未知词转人工；关键词与语义结果做RRF融合，按候选人聚合并重归一化缺失字段权重。 [来源1](https://answers.databricks.com/hays-databricks-build-ai-candidate-job-matching-engine-x_dYacZctsI)

- 【分析／复现建议】复现建议：分别审查不同语言、简历格式、职业间断和资料缺失的召回率及不利影响；不能以模型分数自动淘汰候选人。

- 【分析／复现建议】复现建议：保留来源片段、权重版本和顾问修改记录，限制个人数据访问和保留期限；线上漂移触发重新评估。

### 解决程度与业务提升

- 【公开披露】alpha已发布澳新，演讲报告搜索降至3秒以下。 [来源1](https://answers.databricks.com/hays-databricks-build-ai-candidate-job-matching-engine-x_dYacZctsI)

### 尚未公开的信息

- 【未披露】绝对匹配准确率、招聘成功率变化、偏差测试结果与正式推广覆盖人数未公开。

### 关键技能
- 分析：检索评测与技能本体
- 分析：招聘公平性和人工审阅

### 风险
- 分析：招聘偏差、代理变量和个人数据暴露。

### 限制
- 讲者描述法规设计考量，不等于第三方合规认证。
- 公司每日安置人数不是该新系统的增量成效。

### 来源
1. [Hays and Databricks Build an AI Candidate-Job Matching Engine](https://answers.databricks.com/hays-databricks-build-ai-candidate-job-matching-engine-x_dYacZctsI)
2. [Hays plc Contacts](https://www.haysplc.com/contacts)

## 23. Virtue Foundation：医疗设施基础数据更新与去重

国家：美国；项目落地：未披露
行业：公益与医疗资源信息
国家口径：基金会官方条款给出纽约地址；转录72国指数据覆盖而非系统部署。摘要另写73国，采用正文并保留差异。

概述：人工医疗设施数据库覆盖有限，网页数据嘈杂且重复。

流程：抓取网页→LLM结构化抽取→实体消歧→生成可发布设施数据，供VF Match使用。

落地程度：基础数据更新管线已生产化；数据供VF Match及研究代理使用。

人工职责：基金会规定发布标准，团队维护和验证管线。

证据说明：官方联讲中Michael自述FDE并介绍亲自建设，客户确认共同完成Foundational Data Refresh；非仅公益计划泛述。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 可发布数据规模：40多万条。口径：医疗设施及NGO记录，非患者病历或受益人数。

- 实体消歧任务：23小时未完成→不足1小时。口径：特定倾斜任务；不是全管线速度比。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】既有人工作业形成约3万条设施记录，扩展到百万网页时长任务超时、实体重复与分区倾斜暴露。 [来源1](https://answers.databricks.com/production-scale-healthcare-data-extraction-400k-records-from-5m-web-pages-rQmmMH3EIL0)

### 工程师具体做了什么

- 【公开披露】FDE与基金会及合作团队把数据更新原型推进到生产管线，并移交维护能力。 [来源1](https://answers.databricks.com/production-scale-healthcare-data-extraction-400k-records-from-5m-web-pages-rQmmMH3EIL0)

### 技术方案与数据流程

- 【公开披露】地图与爬虫数据经Spark/Delta入库，Lakeflow拆分提交、轮询、恢复；LLM分步抽取。Splink按名称、位置、国家阻塞候选配对，再加权匹配；salting与Photon缓解热分区。 [来源1](https://answers.databricks.com/production-scale-healthcare-data-extraction-400k-records-from-5m-web-pages-rQmmMH3EIL0)

- 【分析／复现建议】复现建议：为各国建立独立抽样真值，报告缺失地址和未上网设施导致的覆盖盲区；不把“未检索到”当“不存在”。

- 【分析／复现建议】复现建议：保存网页抓取时间和引用、批次ID及幂等状态；设置调用配额和清理策略，不要重复提交整批任务。

### 解决程度与业务提升

- 【公开披露】每次刷新约500万网页，整理40多万条设施/NGO记录，转录覆盖72国；某消歧任务由23小时未完成变为一小时以内。 [来源1](https://answers.databricks.com/production-scale-healthcare-data-extraction-400k-records-from-5m-web-pages-rQmmMH3EIL0)

### 尚未公开的信息

- 【未披露】各国覆盖率、误合并率、抽取准确率及医疗资源配置后的健康成效未披露。

### 关键技能
- 分析：批量提取与幂等恢复
- 分析：概率实体匹配和数据覆盖评测

### 风险
- 分析：医疗设施信息陈旧或实体误合并。

### 限制
- 不采用“全球最大”营销表述。
- 72/73国来源差异已明确，国家数不当部署数。

### 来源
1. [Production-Scale Healthcare Data Extraction: 400K Records from 5M Web Pages](https://answers.databricks.com/production-scale-healthcare-data-extraction-400k-records-from-5m-web-pages-rQmmMH3EIL0)
2. [Virtue Foundation Terms of Service](https://virtuefoundation.org/terms-of-use/)

## 24. AstraZeneca（阿斯利康）：业务域联合代理与权限治理

国家：英国；项目落地：未披露
行业：生物制药
国家口径：集团官方总部资料为英国剑桥；转录举澳新市场查询只是示例，不是部署国证据。

概述：部门自建代理难统一访问、展示与治理，中央应用又易脱离业务。

流程：中央监督代理路由到业务自管的结构化查询或文档问答代理。

落地程度：客户已实施的联合代理平台；覆盖规模未公开。

人工职责：业务团队维护领域语义，中央工程团队管理权限与集成。

证据说明：客户平台工程负责人和AI FDE联合演讲，03:03称共同解决项目问题，32:54明确共同解决OBO认证。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 业务效率变化：未公开。口径：MaxGenie演示的五倍准确率提升不是客户全生产系统成效。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】多个业务代理彼此割裂，投产需要解决授权、统一界面和持续维护。 [来源1](https://answers.databricks.com/multi-agent-architecture-at-scale-astrazeneca-s-agent-bricks-strategy-68gZ-adyLSU)

### 工程师具体做了什么

- 【公开披露】FDE参与跨层身份传递、可视化及持续评测能力；业务保留领域所有权。 [来源1](https://answers.databricks.com/multi-agent-architecture-at-scale-astrazeneca-s-agent-bricks-strategy-68gZ-adyLSU)

### 技术方案与数据流程

- 【公开披露】Agent Bricks supervisor连接Genie及Knowledge Assistant；Entra身份经on-behalf-of传递并由Unity Catalog限制数据访问。Vega-Lite规范随API返回，由前端绘图；MLflow记录轨迹。MaxGenie优化时将题集分为训练、验证和留出测试。 [来源1](https://answers.databricks.com/multi-agent-architecture-at-scale-astrazeneca-s-agent-bricks-strategy-68gZ-adyLSU)

- 【分析／复现建议】复现建议：以不同部门身份重放同一问题，验证每层代理均不能越权；工具返回和缓存也必须按用户权限隔离。

- 【分析／复现建议】复现建议：领域变更后重跑留出题集；同时记录SQL正确率、拒答质量、引用与可视化单位，禁止把失败题全部塞进示例后当泛化提升。

### 解决程度与业务提升

- 【公开披露】客户描述已实施联合平台和领域问答模式，并解决身份传递技术障碍；未给出可信的业务效率量化。 [来源1](https://answers.databricks.com/multi-agent-architecture-at-scale-astrazeneca-s-agent-bricks-strategy-68gZ-adyLSU)

### 尚未公开的信息

- 【未披露】生产代理数量、用户覆盖和节省工时未在转录中明确；不采用页面摘要的20+代理数。

### 关键技能
- 分析：联合代理路由与身份传递
- 分析：留出评测和可观测性

### 风险
- 分析：权限继承失效及跨域语义冲突。

### 限制
- 页面摘要的5→20+代理数未获转录确认。
- 12分钟五倍提升属于优化演示，不作为生产指标。

### 来源
1. [Multi-Agent Architecture at Scale: AstraZeneca’s Agent Bricks Strategy](https://answers.databricks.com/multi-agent-architecture-at-scale-astrazeneca-s-agent-bricks-strategy-68gZ-adyLSU)
2. [AstraZeneca Contact Information](https://www.astrazeneca.com/investor-relations/annual-reports/annual-report-2016/contact-information.html)

## 25. FOX Corporation / FOX One：短视频生成与冷启动推荐

国家：美国；项目落地：未披露
行业：流媒体与媒体
国家口径：FOX官方公司治理页列纽约通讯地址；演讲未逐国披露系统运行区域。

概述：新短视频入口缺少历史互动，内容截取、排序及用户偏好同时冷启动。

流程：从长视频提取短片，离线LLM生成标签，轻量排序模型在线推荐。

落地程度：已上线；规模未公开

人工职责：产品和工程团队做盲审与评测，调整截取和排序约束。

证据说明：FOX产品经理05:08明确FDE嵌入团队；两位FDE在00:57和01:13自述参与该项目。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 个性化链路延迟：低于600毫秒。口径：转录26:47明确已达到；不是单模型推理延迟。

- 每日发布短片：约1200个。口径：生产管线产量；非新增人工节约量。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】新入口几乎没有成熟消费信号，纯规则和端到端在线LLM都难满足目标。 [来源1](https://answers.databricks.com/fox-one-genai-recommendation-system-solving-cold-start-at-scale-vLD1XjcwZnE)

### 工程师具体做了什么

- 【公开披露】FDE与客户共同构建混合式短片与推荐系统，已在FOX One shorts生产使用。 [来源1](https://answers.databricks.com/fox-one-genai-recommendation-system-solving-cold-start-at-scale-vLD1XjcwZnE)

### 技术方案与数据流程

- 【公开披露】Gemini找片段，确定性边界约束修正剪辑；Lakeflow与AI Query批量产生相关性标签及理由，蒸馏至XGBoost。PySpark训练、Model Serving在线评分，Lakebase读取画像和向量；语义相似度与时效特征参与排序。 [来源1](https://answers.databricks.com/fox-one-genai-recommendation-system-solving-cold-start-at-scale-vLD1XjcwZnE)

- 【分析／复现建议】复现建议：把生成标签与真实行为分别评测，维持独立人工盲审；对新闻时间、人物和上下文完整性设门槛，避免截断改变原意。

- 【分析／复现建议】复现建议：分解画像读取、候选生成、评分和重排的尾延迟，严格限制个性化数据使用和保存范围。

### 解决程度与业务提升

- 【公开披露】日识别近3000个候选短片、发布约1200个；讲者确认整条个性化链达到600毫秒以内。 [来源1](https://answers.databricks.com/fox-one-genai-recommendation-system-solving-cold-start-at-scale-vLD1XjcwZnE)

### 尚未公开的信息

- 【未披露】推荐对留存的因果增益、独立偏差测试和长期线上效果未披露。

### 关键技能
- 分析：LLM离线标注与模型蒸馏
- 分析：推荐评测及低延迟服务

### 风险
- 分析：剪辑失真、偏好反馈偏差和冷启动标签失真。

### 限制
- 与FOX Sports搜索是不同产品和工作流。
- 不把Sports AI用户停留时间指标移用于FOX One。

### 来源
1. [Fox One GenAI Recommendation System: Solving Cold Start at Scale](https://answers.databricks.com/fox-one-genai-recommendation-system-solving-cold-start-at-scale-vLD1XjcwZnE)
2. [FOX Statement of Corporate Governance](https://www.foxcorporation.com/corporate-governance/statement-corporate-governance/)

## 26. IFCO：包装资产追踪dbt管线优化

国家：德国；项目落地：未披露
行业：循环包装与物流
国家口径：官方技术文章明确全球总部位于德国Pullach；全球业务50余国不是本系统逐国部署证据。

概述：迟到追踪事件迫使重算历史，核心语义层作业耗时高且难调试。

流程：诊断实际执行计划，修复增量语义，拆分为逐模型任务并自动测试。

落地程度：已上线；规模未公开

人工职责：工程师批准修复，模型负责人负责数据质量。

证据说明：官方技术文章明确IFCO数据平台团队与Databricks FDE共同完成本管线改造。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 核心日作业耗时：约7小时→2小时20分。口径：核心语义层作业，约66%减少；非全平台。

- 日计算费用：降低58%。口径：文章Benchmarking口径；不含完整迁移、维护与人员费用。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】上游每次重写时间戳使几乎全部资产被视为变更，无界窗口及未使用列放大排序和扫描。 [来源1](https://www.databricks.com/blog/scaling-and-operating-large-dbt-project-databricks-ifcos-data-team-performance-visibility-and-debugging)

### 工程师具体做了什么

- 【公开披露】FDE共同定位根因，修正增量处理并移除夜间全量刷新。 [来源1](https://www.databricks.com/blog/scaling-and-operating-large-dbt-project-databricks-ifcos-data-team-performance-visibility-and-debugging)

### 技术方案与数据流程

- 【公开披露】保留真实入库时间、限定重算窗口、删除无用窗口列；按粒度聚簇，逐模型任务并行。诊断skill输出证据及建议，批准后执行并复测；主键和复杂逻辑测试进入CI。 [来源1](https://www.databricks.com/blog/scaling-and-operating-large-dbt-project-databricks-ifcos-data-team-performance-visibility-and-debugging)

- 【公开披露】链接实现读取dbt manifest生成任务DAG，要求生成与运行的项目、适配器版本和解析上下文一致；无法证明选择器精确时拒绝生成。此为工具机制，不证明客户启用了所有选项。 [来源2](https://github.com/mwojtyczka/databricks-dbt-factory)

- 【分析／复现建议】复现建议：为超出窗口的迟到数据设计补算路径；用同一数据快照核对KPI，避免提速来自漏算历史。

### 解决程度与业务提升

- 【公开披露】核心日作业约7小时降至2小时20分，夜间全刷退出；文章报告该优化范围日计算费降低58%。 [来源1](https://www.databricks.com/blog/scaling-and-operating-large-dbt-project-databricks-ifcos-data-team-performance-visibility-and-debugging)

### 尚未公开的信息

- 【未披露】成本绝对额、统计周期、全公司总成本和迟到数据纠错率未公开。

### 关键技能
- 分析：执行计划与增量语义诊断
- 分析：任务图、CI与成本观测

### 风险
- 分析：增量窗口截断导致历史KPI错误。

### 限制
- 开放仓库为检查时版本，不推定是客户部署的精确版本。

### 来源
1. [Scaling and Operating a Large dbt Project on Databricks: IFCO’s Data Team on Performance, Visibility, and Debugging](https://www.databricks.com/blog/scaling-and-operating-large-dbt-project-databricks-ifcos-data-team-performance-visibility-and-debugging)
2. [databricks-dbt-factory：文章直接链接的实现文档](https://github.com/mwojtyczka/databricks-dbt-factory)

## 27. FIS／Amalgamated Bank：反洗钱调查证据装配与案件建议

国家：美国；项目落地：未披露
行业：银行基础设施与反洗钱合规
国家口径：FIS官方说明总部在佛罗里达州Jacksonville；Amalgamated为纽约银行。来源说明美国银行客户与商业供应范围，但未明确实际部署环境所在国家，deploymentCountries留空。

概述：调查员要跨分散系统拼装证据，案件分析之前已耗费大量人工。

流程：连接银行核心系统、汇集证据并结合客户行为分析，生成可追溯建议，调查员作最终决定。

落地程度：2026年10月15日已商业可用，正在Amalgamated部署；不等同已有成熟生产成效。

人工职责：所有输出是建议，关闭案件须分析员明确确认。

证据说明：FIS于5月4日明确点名Anthropic的Applied AI团队及Forward Deployed Engineers，嵌入并共同设计这个Financial Crimes AI Agent；10月15日确认同一产品以AML Investigations Agent名称商业可用。

可切入环节：分析：先验证低风险证据归集与有出处的摘要，保留人工结案。

- 一级告警审查时间：预计减少超过90%。口径：Amalgamated工作流分析预测，非实测。

- 二级案件调查时间：预计减少约98%。口径：Amalgamated工作流分析预测，非实测。

- SAR叙述准备时间：预计减少超过80%。口径：Amalgamated工作流分析预测，非实测。

- 实施投入与净节省：未公开。口径：合同、运行费和收益核算未公开。

### 介入前的问题与基线

- 【公开披露】原流程从相互分离的核心系统收集资料，再由调查员评估活动与已知可疑模式；公告未提供该银行原始耗时分布。 [来源1](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-brings-agentic-ai-to-banking-with-anthropic-starting-with-financial-crimes)

### 工程师具体做了什么

- 【公开披露】Anthropic的前线部署工程师与Applied AI团队进入FIS共同设计首个代理，并交付评测方法及知识转移，使FIS后续能独立扩展。 [来源1](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-brings-agentic-ai-to-banking-with-anthropic-starting-with-financial-crimes)

- 【公开披露】FIS负责数据底座、治理、部署设施与客户关系，Claude承担推理；这是共同建设银行工作流，不只是购买模型调用。 [来源1](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-brings-agentic-ai-to-banking-with-anthropic-starting-with-financial-crimes)

### 技术方案与数据流程

- 【公开披露】5月方案说明：案件启动时经安全连接汇集证据，覆盖FIS及银行自有系统；非FIS核心系统通过开放集成标准接入。 [来源1](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-brings-agentic-ai-to-banking-with-anthropic-starting-with-financial-crimes)

- 【公开披露】10月产品运行于FIS私有云；Control Plane隔离各银行规则和阈值。输出关联原始记录，保留建议和人工决定的审计链。 [来源2](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-aml-investigations-agent-now-commercially-available)

- 【公开披露】原生连接Horizon、Systematics；IBS仍在路线图，不能计作现有集成。 [来源2](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-aml-investigations-agent-now-commercially-available)

- 【分析／复现建议】复现建议，非客户公开实现：以同一批历史案件回放，分别评价证据召回、实体归属、来源准确性和建议可用性；不能只测最终文本是否流畅。

- 【分析／复现建议】复现建议，非客户公开实现：为每家机构单独版本化规则、数据权限和评测集，加入跨租户检索、阈值串用及提示注入测试。

- 【分析／复现建议】复现建议，非客户公开实现：把数据装配、分析、审核、返工分别计时，并记录案件复杂度；先影子运行，再逐项扩大辅助范围。

### 解决程度与业务提升

- 【公开披露】已确认商业发布及首家银行部署进程；当前披露的是能力与预计节时，尚无已完成部署后的对照结果。 [来源2](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-aml-investigations-agent-now-commercially-available)

### 尚未公开的信息

- 【未披露】Claude版本、工具协议、索引与检索架构、评测集规模、验收阈值未披露。

- 【未披露】实测误报／漏报变化、调查员返工、监管验收、故障率、机房国家和净成本未披露。

### 关键技能
- 分析：金融数据映射与证据溯源
- 分析：合规专家协作和案件评测
- 分析：多机构隔离、审计与人工审批设计

### 风险
- 分析：错误归并客户交易可能污染后续判断。
- 分析：来源链完整不等于推理正确；需验证遗漏证据和反例。
- 分析：跨银行配置、阈值或数据串用会构成重大风险。

### 限制
- 三个百分比都是设计伙伴预测，不能标为已经实现。
- BMO只在5月公告中被列为开发伙伴，不另拆一个已部署项目。
- 不将行业AML总支出或误报率当作该项目基线。

### 来源
1. [FIS Brings Agentic AI to Banking with Anthropic, Starting with Financial Crimes](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-brings-agentic-ai-to-banking-with-anthropic-starting-with-financial-crimes)
2. [FIS AML Investigations Agent Now Commercially Available](https://www.fisglobal.com/about-us/media-room/press-release/2026/fis-aml-investigations-agent-now-commercially-available)

## 28. CHI Software（内部运营）：内部简历格式化与运营自动化

国家：未披露；项目落地：未披露
行业：IT服务
国家口径：现有项目来源未确认客户总部国家或实际部署国家；不使用供应商所在地代替。

概述：内部文档与流程靠手工处理，格式不一致，知识分散。

流程：FDE与流程执行者梳理瓶颈，筛选自动化机会，接入原有系统并负责投产；以简历格式化为已量化例子。

落地程度：跨部门计划已有6项投产；14项是已识别机会，不能全部称上线。

人工职责：法务、财务敏感工作要求人工审查；开发前明确权限和升级规则。

证据说明：官方项目页直接写明使用FDE模式，开发团队列Forward Deployed Engineer；这是供应商内部应用，不是外部客户部署。

可切入环节：分析：先复现简历模板转换这一可检查的小流程，再评估其他部门。

- 简历格式化工时：约90分钟降至10分钟，约89%减少。口径：单项任务口径，未披露样本与质量误差。

- 净成本收益：未披露。口径：无实施、模型、维护费及净节省数据。

### 介入前的问题与基线

- 【公开披露】员工手工整理文档与企业模板；简历改格式原需约1.5小时。 [来源1](https://chisw.com/case-studies/ai-transformation/)

### 工程师具体做了什么

- 【公开披露】FDE直接访谈流程执行者，从流程梳理、机会排序到集成投产保持同一责任人；开发前规定权限和升级。 [来源1](https://chisw.com/case-studies/ai-transformation/)

### 技术方案与数据流程

- 【公开披露】公开具体集成是销售尽调与企业格式WBS生成进入Zoho；简历转换已上线。法务和财务保留人工审查。 [来源1](https://chisw.com/case-studies/ai-transformation/)

- 【分析／复现建议】复现建议：将原始简历事实与格式输出分开校验，测试缺字段、表格和非标准日期；这些并非原文披露实现。

### 解决程度与业务提升

- 【公开披露】8部门识别14项机会、6项投产；简历格式化约10分钟，供应商报告89%工时下降。 [来源1](https://chisw.com/case-studies/ai-transformation/)

### 尚未公开的信息

- 【未披露】完整模型、基础设施、各项上线名单、评测样本、错误率与净成本未公开。

### 关键技能
- 流程发现、模板转换、既有系统集成、权限与验收设计

### 风险
- 分析：简历事实失真、文档泄露和敏感审批被误自动化。

### 限制
- 内部案例整体计一例，未将14个机会拆分充数。
- 未公开模型及完整架构，不补写RAG、编排框架或API。

### 来源
1. [CHI官方完整内部FDE转型案例](https://chisw.com/case-studies/ai-transformation/)

## 29. WAIQ（项目品牌；客户法律主体未披露）：多站点标准作业与培训执行平台

国家：未披露；项目落地：未披露
行业：多站点企业运营
国家口径：现有项目来源未确认客户总部国家或实际部署国家；不使用供应商所在地代替。

概述：不同分支流程不一致，知识分散，培训缺少验证，管理者看不到执行准备度。

流程：将标准作业、逐步工作流、培训测验及完成状态统一到多租户平台，按站点、部门、角色控制可见范围。

落地程度：供应商披露已推出并持续运行的平台；客户法律主体、站点数与上线国家不明。

人工职责：分析：运营负责人应批准SOP及培训通过标准；原文未披露具体审批矩阵。

证据说明：官方FDE服务页将WAIQ明确作为工程师进入客户流程和系统、参与站会的实际项目，而非仅展示客户logo。

可切入环节：分析：先选一个跨站点程序，核验版本、人员权限和完成定义。

- 效率量化：未披露。口径：公开了统一流程和实时追踪能力，无前后耗时或合规率数值。

- 成本变化：未披露。口径：无项目价格、维护成本或净节省。

### 介入前的问题与基线

- 【公开披露】分支操作各异，知识散落文档与个人经验，培训没有结构化验证，管理者缺少执行可见性。 [来源1](https://www.hashlogics.com/case-studies/waiq-business-operations-execution-platform)

### 工程师具体做了什么

- 【公开披露】官方FDE经历指出工程师进入WAIQ客户自身系统和流程，围绕各站点完成标准工作并参与站会。 [来源2](https://www.hashlogics.com/hire/forward-deployed-engineers)

### 技术方案与数据流程

- 【公开披露】React、Tailwind CSS前端，PostgreSQL数据层；多租户平台含SOP版本、逐步流程构建、培训测验、站点/部门/角色层级和角色访问控制，仪表板追踪任务与培训状态。 [来源1](https://www.hashlogics.com/case-studies/waiq-business-operations-execution-platform)

- 【分析／复现建议】复现建议：针对跨租户查询、旧版SOP、角色变更及任务重放做测试；具体防护实现未公开。

### 解决程度与业务提升

- 【公开披露】平台推出后持续追踪站点扩展过程中的任务完成、培训和合规状态；未提供量化前后比较。 [来源1](https://www.hashlogics.com/case-studies/waiq-business-operations-execution-platform)

### 尚未公开的信息

- 【未披露】客户法律主体、国家、上线规模、服务端框架、存储与通知接口、审计与隔离实现、成本和效率指标未披露。

### 关键技能
- 多租户与角色权限、组织建模、文档版本、状态与测验数据建模

### 风险
- 分析：跨租户访问、旧版程序仍可执行、测验通过与真实操作能力混淆。

### 限制
- 未见本项目使用特定AI模型的证据；FDE案例不等于生成式AI案例。
- 不将制造、医疗、零售、物流的营销行业标签当成四个已验证客户。

### 来源
1. [Hashlogics官方WAIQ项目全文](https://www.hashlogics.com/case-studies/waiq-business-operations-execution-platform)
2. [Hashlogics官方FDE项目经历说明](https://www.hashlogics.com/hire/forward-deployed-engineers)

## 30. Novo Nordisk（诺和诺德）：临床研发定量分析代理

国家：丹麦；项目落地：未披露
行业：生物制药
国家口径：官方案例将客户国家列为丹麦；没有逐国披露内部使用位置，因此不推定实际部署国家。

概述：临床假设分析依赖稀缺统计专家，探索速度成为瓶颈。

流程：自然语言提出假设，代理生成并执行分析代码，专家验证后用于决策。

落地程度：已内部上线，扩大推广中；未披露覆盖人数。

人工职责：生物统计师和领域专家核验结果。

证据说明：微软官方案例明确该项目由FDE团队AI Acceleration Studio共同开发。

可切入环节：分析：先选可人工核验的单一工作流，再扩大覆盖。

- 季度想法评估能力：5—10个→50多个。口径：负责人报告的探索容量，非临床试验成功数。

- 总投入与净收益：未公开。口径：未披露实施、订阅、维护及人工复核的完整成本，不能据效率指标计算净收益。

### 介入前的问题与基线

- 【公开披露】FounData已整合逾20万患者年的临床试验数据，使用CDISC、SDTM和ADaM标准。 [来源1](https://www.microsoft.com/en/customers/story/26569-novo-nordisk-as-azure)

### 工程师具体做了什么

- 【公开披露】Microsoft FDE与客户共同将Azure推理代理嵌入研发分析流程。 [来源1](https://www.microsoft.com/en/customers/story/26569-novo-nordisk-as-azure)

### 技术方案与数据流程

- 【公开披露】代理对结构化临床数据执行生成代码和统计分析；投产前运行数千项自动测试，并组合查询验证、性能指标、专家审核及用户反馈。 [来源1](https://www.microsoft.com/en/customers/story/26569-novo-nordisk-as-azure)

- 【分析／复现建议】复现建议：将代码执行置于隔离环境，只读访问获准研究数据；固定数据版本与分析脚本，保存统计假设、随机种子和审阅结论。

- 【分析／复现建议】复现建议：按缺失值、混杂因素、亚组样本不足和多重比较构造反例，衡量错误分析率，而非只统计能否生成答案。

### 解决程度与业务提升

- 【公开披露】系统已在内部上线并扩大使用。负责人报告季度可探索的强候选想法从5—10个增至50多个。 [来源1](https://www.microsoft.com/en/customers/story/26569-novo-nordisk-as-azure)

### 尚未公开的信息

- 【未披露】基础模型版本、样本规模、各测试通过率及分析错误率未公开。

- 【未披露】试验成功率提升仍是目标；未披露因该代理而获批的药物或可归因财务回报。

### 关键技能
- 分析：统计分析与代码沙箱
- 分析：专家评测与数据治理

### 风险
- 分析：代码正确运行不代表统计解释有效。
- 分析：敏感研究数据泄露与亚组误判。

### 限制
- 周到分钟为许多探索分析的预期改善，不能当成所有临床研发流程的已审计结果。
- 不得把决策辅助解释为自动临床决策。

### 来源
1. [Novo Nordisk accelerates clinical insight with custom agents on Azure](https://www.microsoft.com/en/customers/story/26569-novo-nordisk-as-azure)
2. [Microsoft Frontier Company：客户领导人证言](https://www.microsoft.com/en-us/frontier-company)

## 31. NFL：NFL Pro Fantasy AI阵容决策助手

国家：美国；项目落地：美国
行业：职业体育与订阅媒体
国家口径：联盟官方地址为美国纽约。实际服务国家按NFL官方产品入口与地域FAQ联合确认：Fantasy AI属于NFL Pro/NFL+ Premium，NFL+仅在美国提供且不含美国属地；该范围指用户服务市场，未推断云数据中心所在地。

概述：NFL要在短周期内把专有比赛数据变成可交互的梦幻橄榄球建议，同时保持面向订阅用户的可靠性。

流程：用户询问球员比较、交易、首发/替补或豁免名单；助手按问题调用统计和新闻数据并生成建议，由用户自行决定阵容。

落地程度：2025赛季已通过NFL Pro向NFL+ Premium用户提供服务；属于生产应用。

人工职责：NFL研究与分析团队参与内容和产品研发；用户获得建议并自行作出阵容选择。未发现自动替用户提交交易或改阵容的项目证据。

证据说明：NFL CIO在AWS官方公告中明确称AWS FDE工程师与联盟团队共同构建NFL Fantasy AI和NFL IQ并投产。本条只记录前者，另有AWS/NFL共同署名论文及客户产品FAQ证明独立工作流。

可切入环节：分析建议：先限定一种阵容问题，建立有时点的数据样本与专家审核标准，再接入实时数据及扩大问题范围。

- 开发至投产：8周。口径：NFL分析负责人在AWS项目文章确认；数天完成的是原型，不能与完整投产混为一谈。

- 专家认可度：>90%。口径：50个分析员编写问题，三轮反馈后获acceptable评级；评审未盲测。

- 响应速度：首token<5秒；完整回答<30秒。口径：论文§5.2，周日上午10倍流量波动下稳定；未给分位数。

- 联合推理优化：token减少70%；吞吐2倍；推理费降低45%。口径：语义压缩、缓存及工具输出结构共同优化的结果；不是项目总成本。

- 观测到的越界输出：逾10,000次生产查询中为0。口径：论文所述离题及政策违规；不是未来零风险保证。

- 总投入与净收益：未公开。口径：未给实施合同费、完整运营成本或可归因的订阅收入增量。

### 介入前的问题与基线

- 【公开披露】产品要把Next Gen Stats、球员新闻、天气及其他NFL资料用于个性化建议，交付需兼顾速度和可靠性。 [来源4](https://aws.amazon.com/blogs/machine-learning/accelerate-enterprise-solutions-with-agentic-ai-powered-consulting-introducing-aws-professional-service-agents/)

### 工程师具体做了什么

- 【公开披露】NFL CIO直接将Fantasy AI列为AWS FDE与内部工程团队共同建设的产品，确认工程师参与实际投产。 [来源1](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers)

- 【公开披露】项目使用Professional Services Delivery Agent自动化常规开发，NFL团队集中处理性能与专有数据洞察；数天原型、八周投产是两个阶段。 [来源4](https://aws.amazon.com/blogs/machine-learning/accelerate-enterprise-solutions-with-agentic-ai-powered-consulting-introducing-aws-professional-service-agents/)

### 技术方案与数据流程

- 【公开披露】EKS接入，Strands与Bedrock编排，MCP接NGS及RotoWire；系统提示保存分析方法，21类语义字典指导取数。模型迭代压缩字段/工具说明，29个工具并为10个；另有缓存、模型回退和主题护栏。 [来源2](https://www.amazon.science/publications/encoding-domain-expertise-in-agents-lessons-from-nfl-fantasy-ai)

- 【分析／复现建议】复现建议，非客户已公开实现：把数据时间、字段含义与推荐依据一起保存；在训练/调优之外留出新赛季及突发伤情题，避免用反复修改的验收集代表泛化能力。

- 【分析／复现建议】复现建议，非客户已公开实现：分别监测首token、完整回答和工具取数延迟；缓存失效要与伤情和阵容变化联动，模型回退后重新验证建议质量。

- 【分析／复现建议】复现建议，非客户已公开实现：上线时限制建议范围，使用只读工具；如果今后增加阵容修改或交易操作，须另设权限和用户确认。

### 解决程度与业务提升

- 【公开披露】官方产品说明确认用户可获得球员、交易、首发及豁免名单建议，机器人只回答梦幻橄榄球相关问题。 [来源3](https://support.nfl.com/hc/en-us/articles/42933830263316-What-is-Fantasy-AI-Assistant-powered-by-AWS)

- 【公开披露】本条专家认可、响应速度、联合推理优化和越界输出指标均据论文§3与§5；具体数值及测量限制见指标栏。 [来源2](https://www.amazon.science/publications/encoding-domain-expertise-in-agents-lessons-from-nfl-fantasy-ai)

- 【分析／复现建议】分析：价值在于把分散数据转成可追问的订阅产品体验；已有交付与技术指标，尚不能证明订阅增收或用户比赛成绩改善。

### 尚未公开的信息

- 【未披露】正式上线模型版本、每次请求绝对成本、服务地区之外的数据驻留位置及合同金额未公开。

- 【未披露】未公开受控的用户留存、付费转化或实际梦幻比赛结果对比。

### 关键技能
- 分析：专家访谈与领域判断抽象
- 分析：语义工具接口设计及API集成
- 分析：峰值容量、回退和端到端性能评测

### 风险
- 分析：伤情、阵容和比赛消息时效过期会改变建议。
- 分析：演示问题反复调优后可能高估泛化表现。
- 分析：建议可能被误当保证结果，产品需要明确不确定性。

### 限制
- 与NFL IQ的球队/选秀问答是不同产品；不借用IQ的6周或16.8万用户指标。
- 专家认可不等于赛后预测准确率；论文未做组件消融，不能把共同成果单独归因于FDE或某个优化。

### 来源
1. [AWS官方：投入10亿美元建设前线部署工程组织](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers)
2. [AWS与NFL联合论文：Encoding domain expertise in agents: Lessons from NFL Fantasy AI](https://www.amazon.science/publications/encoding-domain-expertise-in-agents-lessons-from-nfl-fantasy-ai)
3. [NFL官方：Fantasy AI Assistant功能说明](https://support.nfl.com/hc/en-us/articles/42933830263316-What-is-Fantasy-AI-Assistant-powered-by-AWS)
4. [AWS官方：Professional Services Delivery Agent的NFL交付实例](https://aws.amazon.com/blogs/machine-learning/accelerate-enterprise-solutions-with-agentic-ai-powered-consulting-introducing-aws-professional-service-agents/)
5. [NFL官方：NFL+服务国家范围](https://support.nfl.com/hc/en-us/articles/35869824536724-Where-is-NFL-available)
6. [NFL官方：联盟地址](https://support.nfl.com/hc/en-us/articles/35869693160980-League-Address)

## 32. NHS England（英国国家医疗服务体系英格兰分部）：疫情数据底座与医疗物资、疫苗运营

国家：英国；项目落地：英国
行业：公共卫生应急与医疗物资供应
国家口径：英国新冠调查正式证词第1—4、28、38段明确机构主体及英格兰医院和疫苗项目；英国为主体国，实际范围明确为英格兰，不扩大为英国所有地区。

概述：疫情初期库存、床位、人员和需求数据分散，人工电话与表格难以支持每日资源分配。

流程：Foundry集成医院和国家库存数据；建立床位、病例和库存视图；支持每日呼吸机与个人防护装备（Personal Protective Equipment）分配会议；同一底座后来支持疫苗站点准备、订货配送及接种覆盖监测。

落地程度：2020年3月起数据底座投入疫情响应；4月支持物资分配；证词确认后续疫苗运营使用。作为一个疫情响应项目收录，不将多个模块拆成案例。

人工职责：医院报送或连接库存；国家医疗服务体系人员负责分配决策，供应商工程师参加业务会议；信息治理团队设置访问、最小化及审计控制。

证据说明：官方调查收录供应商宣誓证词：第12段指出数据底座由前线部署工程师（Forward Deployed Engineer）Gemma Hallatt带队；第19、25段明确Tom McArdle、Joanna Peller均为前线部署工程师并带队参与呼吸机、防护物资分配。

可切入环节：从单地区库存可视化和人工确认的调拨建议开始。

- 数据接入范围：数百个数据源。口径：证词第14段指疫情数据底座，非全部系统独由Palantir提供。

- 疫苗项目服务范围：英格兰超过4400万人。口径：证词第38段；这是疫苗项目覆盖人数，不是软件单独造成的新增接种人数。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】疫情初期库存、床位、人员与需求信息分散，原记录引用证词描述电话和表格难以支撑每日调度。本轮证词原PDF返回403，未重新读取全文；以下保留已有记录的证据边界。 [来源1](https://covid19.public-inquiry.uk/wp-content/uploads/2025/03/11180002/INQ000536417.pdf)

### 工程师具体做了什么

- 【公开披露】原记录引用证词第12、19、25段，分别将数据底座、呼吸机及防护物资工作与具名前线部署工程师及团队相连；不是只凭供应商签约认定FDE参与。 [来源1](https://covid19.public-inquiry.uk/wp-content/uploads/2025/03/11180002/INQ000536417.pdf)

### 技术方案与数据流程

- 【公开披露】已有记录中的数据链路为医院及国家库存数据进入Foundry，形成病例、床位和库存视图，供每日分配会议使用；后续同一底座支持疫苗站点、订货配送和覆盖监测。原记录明确物资分配不等于参与PPE采购。 [来源1](https://covid19.public-inquiry.uk/wp-content/uploads/2025/03/11180002/INQ000536417.pdf)

- 【分析／复现建议】复现建议，非客户已公开实现：为医院、物资品类、库存快照、需求及调拨单设置稳定标识；区分缺失、迟报和真实零库存，界面同时显示更新时间与责任机构。

- 【分析／复现建议】复现建议，非客户已公开实现：将预测需求和现存库存分别呈现；记录调拨建议、人工决定与实际签收。审批日志需要同时保留当时数据版本，才能解释应急决策。

### 解决程度与业务提升

- 【公开披露】已有记录报告数百个数据源，以及疫苗项目服务英格兰超过4400万人；前者是集成规模，后者是公共项目覆盖，均不能解释为软件独立创造的健康收益。 [来源1](https://covid19.public-inquiry.uk/wp-content/uploads/2025/03/11180002/INQ000536417.pdf)

### 尚未公开的信息

- 【未披露】本轮无法重新核验原证词全文，不能称已完成全部一手材料复审。NHS官方数据存储说明页也返回机器人验证；未绕过限制。

- 【未披露】现有可核材料未给出预测模型、优化函数、字段映射、刷新频率、质量阈值或准确率；不得据Foundry品牌推定使用大语言模型。

- 【未披露】现有记录未给出各阶段合同费用、人员投入与净节省。这里的“未公开”仅指引用证据未能支持，不断言不存在公开采购合同。

- 【未披露】患者级数据边界、实际权限配置及审计验证结果未由本轮材料复核，不能从一般平台能力推定全部控制已落实。

### 关键技能
- 公共卫生数据集成
- 库存与需求建模
- 权限及数据溯源
- 与每日调度会议共同迭代

### 风险
- 敏感健康数据与跨机构权限
- 库存迟报及需求估计误差可能影响公平分配

### 限制
- 供应商证词不是独立因果评估。
- 证词明确Palantir没有参与个人防护装备采购；不将物资分配写成采购系统。
- 不是生成式人工智能案例；未将不同疫情模块拆分计数。

### 来源
1. [Louis Mosley代表Palantir Technologies UK的英国新冠调查证词](https://covid19.public-inquiry.uk/wp-content/uploads/2025/03/11180002/INQ000536417.pdf)

## 33. The Elmet Group：钨钼及微波器件制造的经营、成本与排程系统

国家：美国；项目落地：美国
行业：特种金属与工业微波器件制造
国家口径：集团2026-09-08官方证券申报列总部缅因州波特兰；客户访谈说明工程师到缅因州现场，制造基地位于缅因、俄亥俄、密歇根。只确认美国，未把矿料来源国当作部署国。

概述：原有业务数据与工厂流程割裂，管理层难以快速了解订单成本、工作票位置和利润。

流程：接入业务系统，将材料清单、销售订单、工票、工序和设备连接成运营对象；建立成本、利润、生产进度与排程应用。

落地程度：客户称两个月在集团两个业务部推出10个应用；未公开各应用用户数或持续使用率。

人工职责：采购、供应链、生产及工厂经理与工程师共同定义首批优先事项；经理使用成本与排程信息作决定。

证据说明：客户Scott Knoll在AIPCon 11访谈明确4名Palantir工程师于6月中旬赴现场，与采购、生产经理共同梳理优先级并交付应用；官方页面与视频确认项目。工程师现场参与证据明确，转写未独立复听。

可切入环节：先连接一个工厂的订单、工票及成本数据，由生产经理验证。

- 交付范围：约2个月，2个业务部，10个应用。口径：Scott Knoll客户自报；应用数量不等于独立项目数。

- 首批交付周期：约3—4周。口径：客户访谈描述首批数据和应用交付，不是整个集团改造完成。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】集团沿用旧ERP且资本受限，需要看清订单成本、工票位置、利润及排程。原记录明确是两个业务部的制造运营，不是替换所有ERP。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

### 工程师具体做了什么

- 【公开披露】四名工程师赴缅因州与采购、生产和总经理共同确定优先事项；约3—4周交付首批，约两个月推出10个应用。应用数不等于十个独立案例。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

### 技术方案与数据流程

- 【公开披露】数据关系覆盖展开后的材料清单、销售订单、工票、工序、设备及成本；经理据此检查生产位置和排程。客户另提在个人沙箱用历史CRM预测报价成交，不能将该探索并入已上线制造模型。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

- 【分析／复现建议】复现建议，非客户已公开实现：按订单—材料清单版本—工票—工序—设备建立关联，显式处理替代材料、报废和返工；先让工厂经理核对样本订单的实际成本，再推广成本视图。

- 【分析／复现建议】复现建议，非客户已公开实现：把排程可行性与模型评分分开验收：检查设备能力、维护窗口、工序前后依赖、批量及材料到货；建议发布前由生产负责人确认。

- 【分析／复现建议】复现建议，非客户已公开实现：如评估CRM成交模型，应按时间切分历史报价，避免把后续销售活动或已知成交结果泄漏到输入；这不是已披露的客户评测流程。

### 解决程度与业务提升

- 【公开披露】可量化披露主要是应用交付速度和范围；没有可比较的准时交付率、单位成本或产能改善数据，不能把“更快建应用”换算为制造净收益。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

### 尚未公开的信息

- 【未披露】ERP产品、连接方式、数据同步延迟、主数据去重和历史成本回算规则未披露。

- 【未披露】生产排程是否采用优化器、模型名称、报价预测训练集与准确率未披露；未披露生产写回权限和异常停机机制。

- 【未披露】客户对安全框架的口述不是独立合规认证审计；合同金额、运维成本及各应用活跃使用率未披露。

### 关键技能
- 制造业务访谈
- 材料清单与工序建模
- 多系统数据接入
- 成本核算与排程交互设计

### 风险
- 成本口径和材料主数据不一致
- 排程建议需要考虑真实产线约束

### 限制
- 交付速度为客户自报，缺少独立审计。
- 不将客户探索中的个人报价预测原型视为全公司生产部署。

### 来源
1. [Sippin’ Sovereignty：The Elmet Group at AIPCon 11](https://www.youtube.com/watch?v=4j8qdjGd6cA)
2. [AIPCon 11参与者演讲和访谈转写](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)
3. [The Elmet Group官方8-K申报](https://investors.theelmetgroup.com/sec-filings/content/0001213900-26-097862/ea0304152-8k_elmet.htm)
4. [Elmet Technologies制造基地](https://www.elmettechnologies.com/about-elmet/locations/)

## 34. NVIDIA：芯片到计算交付的供应链控制塔

国家：美国；项目落地：未披露
行业：半导体与人工智能计算系统制造
国家口径：NVIDIA官方联系页列公司总部圣克拉拉。项目材料说明内部供应链与本地硬件部署，但未明确部署服务器或使用团队的国家清单，实际落地国家留空。

概述：半导体、机柜和客户计算交付跨多层供应商，约束与变更难以在分散系统中同步。

流程：Foundry与Ontology连接供应链对象；人工智能平台（Artificial Intelligence Platform）结合约束求解器和经过企业数据后训练的NVIDIA模型，辅助规划者分析缺料、分配与履约取舍，并把人工调整反馈给工作流。

落地程度：2026年9月客户与供应商展示已部署的内部供应链系统和后训练能力；仍在早期共同扩展阶段，不等于全供应链无人化。

人工职责：规划者设定业务约束、检视建议并处理取舍；工程师与供应链专家共同建模及迭代。

证据说明：NVIDIA供应链副总裁Jeff Whitmer在AIPCon 11针对前线部署工程师（Forward Deployed Engineer）的问题，描述工程师与其团队共同建模；Palantir工程师Sid Singh另述带产品团队到NVIDIA现场共建。官方视频确认具体供应链项目。

可切入环节：先选择一个物料短缺处置流程，以只读建议和人工审批开始。

- 可独立核实的运营提升：未公开。口径：未披露完整观察期、产出基线或独立审计的成本/交付改善比例。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】供应链团队每周重排关键物料分配；缺一类组件就可能阻塞组装，提前到货的其它物料继续占用库存。优化目标是Time of Ownership，即物料入厂到随产品离厂的时间。 [来源6](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

### 工程师具体做了什么

- 【公开披露】客户和工程师共同建模；Sid Singh说明把产品团队带到NVIDIA现场。FDE角色来自演讲转写，不是从技术文章作者身份推定。 [来源4](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

### 技术方案与数据流程

- 【公开披露】Ontology关联物料、工厂、承诺、产能、分配及定性信号；cuOpt从中取数，求解最小化库存占用时间的混合整数线性规划并写回分配及约束。 [来源6](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

- 【公开披露】专家决定、理由和结果成为训练记录；NeMo Anonymizer去敏，Data Designer扩充样例，AutoModel以LoRA微调Nemotron 3.5 Lightning，基础权重冻结。Autopilot保留数据—模型—建议溯源。 [来源6](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

- 【公开披露】回测只给决策当日已知信息，隐藏结果；模型建议由规划者最终决定，接受、编辑、推翻及实际结果回写。强化学习仍是未来方向，生产模型不会自行训练。 [来源6](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

- 【分析／复现建议】复现建议，非客户已公开实现：除与专家一致率外，分开量化提前备料、缺料停线和承诺违约的实际代价；不要把复制历史选择当作业务最优性的充分证明。

### 解决程度与业务提升

- 【公开披露】开发基准准确率86.7%，平衡准确率58.6%、Macro-F1为57.5%；这不等于真实交付改善86.7%。作者承认未来生产风险预测仍困难。 [来源6](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

### 尚未公开的信息

- 【未披露】未提供评测样本量、时间区间、独立测试集和逐类别混淆矩阵，不能据开发集指标认定广泛泛化。

- 【未披露】未给出上线后库存占用时间、吞吐量、规划工时的可比较变化及总费用；训练快不能代替净成本计算。

- 【未披露】具体接入系统、访问授权矩阵、部署地点、实际推理延迟、发布阈值及回滚程序未披露。

### 关键技能
- 供应链本体建模
- 约束优化与人工智能协作
- 本地部署与模型后训练
- 规划者反馈回路

### 风险
- 错误供应或约束数据会传导至生产计划
- 商业机密、模型权限与人工覆盖决策记录

### 限制
- 前线参与依据客户和工程师一手发言的第三方转写，未复听原视频。
- 未把10倍规划者生产力愿景或模型基准表现当作已实现供应链成效。

### 来源
1. [Palantir Sovereign AI For NVIDIA’s Supply Chain](https://www.youtube.com/watch?v=PeaDoeI4n-8)
2. [Sovereign AI for the Compute Supply Chain](https://www.youtube.com/watch?v=xZBaOenSZ9I)
3. [Sippin’ Sovereignty技术访谈](https://www.youtube.com/watch?v=O65qIwMLAqI)
4. [AIPCon 11参与者演讲和访谈转写](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)
5. [NVIDIA联系与总部地址](https://www.nvidia.com/en-us/contact/)
6. [NVIDIA技术团队：供应链决策、cuOpt与Nemotron后训练](https://developer.nvidia.com/blog/from-wafer-out-to-first-token-codifying-supply-chain-expertise-with-nemotron-and-palantir-foundry)

## 35. Acrisure：Auris AI保险经纪运营系统

国家：美国；项目落地：美国
行业：保险经纪与风险服务
国家口径：Acrisure官方办公室页列总部密歇根州Grand Rapids；Benjamin Funk演讲列共同部署城市包括Grand Rapids、Chicago、New York等美国城市。集团19国业务不等于本项目已在19国上线。

概述：通过大量收购形成的保险经纪网络存在客户、承保公司和服务系统分散的问题。

流程：将客户风险、合同、承保公司、报价和服务需求统一建模；辅助发现保障缺口、准备投保资料、比较报价并路由服务工作。

落地程度：2026年9月发布并展示实际业务工作流；未公开全集团生产覆盖率或每项自动化的上线批次。

人工职责：客户顾问、保险安排专家和服务人员保留业务判断；工程师与业务人员现场共同建设，权限约束数据与操作。

证据说明：客户技术负责人Benjamin Funk在AIPCon 11将当前Auris项目明确连接到前线部署工程（Forward Deployed Engineering），说明双方工程师和分析师赴多地与业务团队共同建设；不是依据其本人过去在Palantir的任职经历。官方发布与第一人称演讲转写组成B级证据。

可切入环节：先做材料完整性检查和可追溯的报价对比，交保险专业人员确认。

- 运营效果：未公开可比较数值。口径：发布材料主要描述能力和工作流，未给出可独立比较的生产率或损失率变化。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】保险工作跨客户、承保公司、合同与运营数据，系统及流程割裂；官方定位是把这些信息放入受权限控制的共同运营环境。 [来源5](https://markets.financialcontent.com/stocks/article/bizwire-2026-9-10-acrisure-unveils-auris-ai-a-new-ai-operating-system-in-the-insurance-industry)

### 工程师具体做了什么

- 【公开披露】客户自己的技术团队与业务人员基于Ontology和AIP建设；演讲明确双方工程师及分析师到多个美国城市共同改进核心保险流程。 [来源3](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/) [来源5](https://markets.financialcontent.com/stocks/article/bizwire-2026-9-10-acrisure-unveils-auris-ai-a-new-ai-operating-system-in-the-insurance-industry)

### 技术方案与数据流程

- 【公开披露】发布稿将客户洞察、风险、安排保险、服务需求和承保公司关系纳入共享环境；它并未公布底层字段映射或具体模型。 [来源5](https://markets.financialcontent.com/stocks/article/bizwire-2026-9-10-acrisure-unveils-auris-ai-a-new-ai-operating-system-in-the-insurance-industry)

- 【公开披露】演讲中的The Exchange连接承保门户、邮件、评级引擎、计算机操作与MCP；专业人员选择市场及报价并保存理由，服务阶段保留人工确认。属于演示工作流，不保证每条链路全面投产。 [来源3](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)

- 【分析／复现建议】复现建议，非客户已公开实现：将客户事实、保险条款原文、模型推断与人工意见分开存储；比较报价时保留免赔额、除外责任及生效日期，避免只按保费排序。

- 【分析／复现建议】复现建议，非客户已公开实现：对跨承保公司操作使用最小权限，并把提交报价、绑定保障、生成文件各设独立授权与重试状态，避免重复提交或错误绑定。

- 【分析／复现建议】复现建议，非客户已公开实现：评测应覆盖缺失人员清单、过期条款、同名客户和不同格式报价，分别记录抽取错误及专业人员推翻建议的原因。

### 解决程度与业务提升

- 【公开披露】官方确认发布及生产方向，但声明实际能力和效果依用例、数据与实施而异；没有可比较的转化率、周转时间或净收益，不把集团规模当采用人数。 [来源5](https://markets.financialcontent.com/stocks/article/bizwire-2026-9-10-acrisure-unveils-auris-ai-a-new-ai-operating-system-in-the-insurance-industry)

### 尚未公开的信息

- 【未披露】模型供应商及版本、微调与检索策略、标注数据、评测集规模和失败率未披露。

- 【未披露】各演示环节上线批次、服务代理自主执行范围、细粒度租户隔离和第三方授权控制未披露。

- 【未披露】合同金额、推理费用、错误保险决定的返工成本及净节省未披露。

### 关键技能
- 保险对象与业务规则建模
- 非结构化投保材料处理
- 跨公司数据权限
- 业务现场共同设计

### 风险
- 敏感客户资料泄露
- 错误保障缺口或报价比较影响保险决策

### 限制
- 一手演讲通过第三方转写核验；未独立复听。
- 不把集团员工、国家或收购数量写为本项目采用人数。

### 来源
1. [Connecting the Insurance Industry with Auris AI](https://www.youtube.com/watch?v=HPUVkVmIitA)
2. [Acrisure官方发布的演讲说明](https://www.linkedin.com/posts/acrisure_connecting-the-insurance-industry-with-auris-activity-7505249848829440001-lH_p)
3. [AIPCon 11参与者演讲和访谈转写](https://stockanalysis.com/stocks/pltr/transcripts/750256-aipcon-11/)
4. [Acrisure办公室与总部](https://www.acrisure.com/locations)
5. [Acrisure官方发布：Auris AI保险运营平台](https://markets.financialcontent.com/stocks/article/bizwire-2026-9-10-acrisure-unveils-auris-ai-a-new-ai-operating-system-in-the-insurance-industry)

## 36. Joint Commission：Reforge认证检查员排班与标准知识平台

国家：美国；项目落地：美国
行业：医疗质量认证与现场评审
国家口径：Joint Commission官方联系页明确总部在美国伊利诺伊州Oakbrook Terrace；客户演讲明确美国医疗认证、州执照及美国天气事件下的实际排班，未据全球业务推断其他国家上线。

概述：检查员专业资格、执照、位置和可用时间存在大量约束，原本依靠表格和少数人员经验安排评审。

流程：统一检查员、机构、执照、标准与日程；求解器生成排班，并在天气等事件下重排或取消；将认证标准整理成可公开查询的知识平台。

落地程度：客户确认排班与标准功能已实际使用；排班应用建设约8个月。实时自动认证评分仍为下一阶段愿景。

人工职责：排班团队设置约束并管理改期；医学专家仍执行现场检查与认证判断；现场演示使用非真实数据保护机构隐私。

证据说明：客户数字与信息负责人William Walders在AIPCon 9点名前线部署工程师（Forward Deployed Engineer）并再次称5位工程师对Reforge至关重要；客户官方合作公告确认认证平台项目。

可切入环节：先统一检查员资格与可用时间，生成由排班员审核的方案。

- 排班计算：过去数周，现约3分钟。口径：客户口述；指生成计划时间，不等于整个认证周期。

- 覆盖检查员：约600名。口径：同一演讲描述求解器的排班规模，非新增员工或全部自动完成检查。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】检查员资格、执照、位置与可用时间原散在系统、表格和团队经验中，排班需数周；不是一般日历排时间，还需匹配医疗机构的检查专业要求。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

### 工程师具体做了什么

- 【公开披露】客户点名约五位FDE；排班应用建设约八个月。客户本人另感谢内部Reforge技术团队及Palantir协作，强调工作仍处早期并持续推进。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/) [来源4](https://www.linkedin.com/posts/walders_aipcon-reforge-activity-7441149075061813248-foEz)

### 技术方案与数据流程

- 【公开披露】Ontology连接检查员资格、机构、许可及日程，Solver生成安排；标准知识进入Foundry并公开查询，天气事件可触发重排或取消。现场展示采用非真实机构数据。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

- 【公开披露】客户转发的供应商说明进一步提到双向写回、求解优化和代理流程，但没有披露每个目标系统的接口或事务处理。 [来源4](https://www.linkedin.com/posts/walders_aipcon-reforge-activity-7441149075061813248-foEz)

- 【分析／复现建议】复现建议，非客户已公开实现：将执照有效期和专业资质作为硬约束，将差旅费用与偏好作为软目标；对无可行解给出冲突解释，禁止静默放松法定条件。

- 【分析／复现建议】复现建议，非客户已公开实现：每次排班应版本化保存输入、约束、审批人及取消通知状态，风暴下批量改动也需能恢复和逐项核对。

### 解决程度与业务提升

- 【公开披露】客户报告约600名检查员的计划生成从数周降到约三分钟；仅为排班计算/准备口径，不是现场认证检查耗时。实时认证与压缩3—5天到访仍是未来设想。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

### 尚未公开的信息

- 【未披露】Solver产品、数学目标、硬软约束清单、求解质量及历史计划回测结果未披露。

- 【未披露】标准查询的检索/模型架构、引用正确率、标准更新审核程序和实际写回权限未披露。

- 【未披露】排班员实际工时、差旅节省、认证质量变化和总项目费用未披露，不能从三分钟推导全部业务成本下降。

### 关键技能
- 人员资格和执照建模
- 约束排班
- 标准知识整理
- 敏感机构数据隔离

### 风险
- 排班约束遗漏导致资质不符
- 认证标准版本和权限错误

### 限制
- 参与角色和实际成效来自客户一手演讲转写，未独立复听。
- 不将未来实时认证或缩短3—5天现场检查写成已实现结果。

### 来源
1. [Joint Commission与Palantir官方合作公告](https://www.jointcommission.org/en/knowledge-library/newsletters/joint-commission-online/14-may-25)
2. [AIPCon 9参与者演讲转写](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)
3. [Joint Commission联系页](https://www.jointcommission.org/en-us/contact-us)
4. [William Walders本人对Reforge建设团队及阶段的说明](https://www.linkedin.com/posts/walders_aipcon-reforge-activity-7441149075061813248-foEz)

## 37. GE Aerospace：航空发动机供应约束识别与生产协同

国家：美国；项目落地：美国
行业：航空发动机制造与维修保障
国家口径：GE官方2026-03-09公告明确总部辛辛那提；客户演讲说明6名前线部署工程师到辛辛那提处理内部供应链。国际机队扩展未逐国披露，不据全球销售推断部署国。

概述：关键零件短缺会拖延发动机维修和新机交付，原来团队需每周手工拼接多套系统的数据。

流程：整合企业资源规划（Enterprise Resource Planning）、产品生命周期管理（Product Lifecycle Management）、供应商与计划数据，识别未来约束并向运营人员推荐处置；从J85保障经验扩展到内部制造。

落地程度：2024年J85试点；2025年扩大内部供应链应用；2026年继续扩展代理式工作流。工程师现场证据直接对应内部供应链扩展。

人工职责：运营与供应链负责人处理系统发现的约束；工程师对接数据和业务模型；精益管理与人工专业判断同时参与。

证据说明：客户AIPCon 9演讲明确称Palantir在下一周派6名前线部署工程师（Forward Deployed Engineer）到辛辛那提共同解决内部供应约束；GE官方公告确认从J85保障试点扩展到企业生产系统。

可切入环节：选取一类发动机关键短缺件，将预警与人工供应商处置流程连接。

- 数据准备工作：此前多名人员每周一各耗约8小时拼表。口径：客户提供旧工作方式；新流程近实时推送约束，未披露实际节省工时总量。

- 发动机产出：2025年同比增加26%。口径：客户明确归于技术与FLIGHT DECK精益运营共同作用；不可单独归因于Palantir或工程师。

- 项目成本：未公开。口径：未披露合同费、实施人力成本、推理费用及净节省。

### 介入前的问题与基线

- 【公开披露】J85保障试点针对零件需求与短缺；内部团队原需每周一多人各花约八小时拼表找瓶颈。发动机少一件关键零件便可能延迟维修或装配。 [来源1](https://www.geaerospace.com/news/press-releases/ge-aerospace-and-palantir-expand-partnership-transform-military-aircraft-readiness) [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

### 工程师具体做了什么

- 【公开披露】客户称六名FDE次周到辛辛那提；团队将ERP、计划、PLM和供应商系统连接到同一运营对象模型。官方确认从2024年J85扩展到内部生产，而非两个独立案例。 [来源1](https://www.geaerospace.com/news/press-releases/ge-aerospace-and-palantir-expand-partnership-transform-military-aircraft-readiness) [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

### 技术方案与数据流程

- 【公开披露】官方说明覆盖选定供应链功能：履约、采购、分配、维修及客户服务；以企业数据预测需求和提前识别约束，代理处理重复工作，人员解决业务问题。不能据此认定所有部门都已无人化。 [来源1](https://www.geaerospace.com/news/press-releases/ge-aerospace-and-palantir-expand-partnership-transform-military-aircraft-readiness)

- 【分析／复现建议】复现建议，非客户已公开实现：把每条短缺预警链接到零件版本、发动机配置、供应承诺及修理需求；记录为何某件缺料影响某一发动机，而不只输出排行榜。

- 【分析／复现建议】复现建议，非客户已公开实现：将预警提前量与误报率按3、6、12个月分别评测，并按零件替代性和安全影响分层；不以找到更多风险代替实际修复瓶颈。

- 【分析／复现建议】复现建议，非客户已公开实现：处置建议应指向采购或供应商行动责任人，完成后回收实际交付结果；军民项目的数据及可见范围需单独验收。

### 解决程度与业务提升

- 【公开披露】领导者现在得到近实时约束信息。2025年发动机产出增长26%由客户归于技术与FLIGHT DECK精益运营共同作用；不能单独归因FDE或Palantir，也不是单位成本降幅。 [来源2](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)

### 尚未公开的信息

- 【未披露】未披露具体大模型、预测器、优化方法、知识检索方式、误报漏报或验收集。

- 【未披露】接口刷新频率、推荐动作的自动批准边界、回写/回滚方式及军民数据隔离配置未披露。

- 【未披露】J85就绪率和内部生产的可比较归因指标、实施费用、软件费及净收益未披露。

### 关键技能
- 多系统供应链集成
- 零件和维修需求建模
- 约束预警
- 生产团队反馈闭环

### 风险
- 关键零件预测错误
- 军民业务数据边界及权限

### 限制
- 客户一手发言通过第三方转写读取，未独立复听。
- 不将J85试点和内部扩展拆成两例。
- 产出增长不是软件单独因果效果，也不是成本降幅。

### 来源
1. [GE Aerospace与Palantir扩展合作官方公告](https://www.geaerospace.com/news/press-releases/ge-aerospace-and-palantir-expand-partnership-transform-military-aircraft-readiness)
2. [AIPCon 9参与者演讲转写](https://stockanalysis.com/stocks/pltr/transcripts/598492-aipcon-9/)
3. [GE官方美国制造投资公告](https://www.geaerospace.com/news/press-releases/ge-aerospace-invest-another-1b-us-manufacturing)

## 38. AIG：投保资料整理与核保助手

国家：美国；项目落地：未披露
行业：财产与商业保险
国家口径：American International Group美国证券监管年报列公司总部位于纽约。当前引用的核保助手材料没有逐国列明本流程部署范围，国家字段只表达主体总部；不从险种名称或公司业务版图推断上线国。

概述：核保师需从分散投保材料和内外部数据中整理风险摘要，资料准备占用时间。

流程：Underwriter Assistance对投保材料进行提取、外部和内部数据增强、风险优先级排序与摘要，供核保师决定报价／承保。

落地程度：2025-03-31投资者日：已在Financial Lines Private Not-for-Profit投入生产；其它险种扩展与Claims Assistance当时仍在推进，不一概算全面生产。

人工职责：官方p117-118明示Underwriter analyzes AI output之后才Quote/Bind/Book/Issue；p124 HITL核实/更正检索答案。

证据说明：CEO在AIPCon访谈针对 FDE（Forward Deployed Engineer，前线部署工程师）的问题描述工程师全程与业务/技术团队共同迭代。角色证据由访谈转写读取，本次原视频未能直接复核；官方投资者资料独立证实该核保流程生产使用。

可切入环节：仅做固定险种的材料完整性检查与有引用摘要，报价、绑定及出单留给核保师。

- 核保资料摘要准备：少于1天。口径：2025投资者材料第118页；只到准备好供核保师审核，不是全流程承保少于一天。

- 人员容量：无需新增FTE可增加容量。口径：公司定性陈述；增幅、观察期和实际人均产出未公开。

- 成本变化：未公开。口径：无总实施费、核保单件净成本或净节省披露。

### 介入前的问题与基线

- 【公开披露】核保前需要从非标准投保资料及内外部来源提取、整理风险信息；2025投资者资料确认Financial Lines的Private Not-for-Profit已生产，其它险种仍扩展中。不能把规划推广范围当已上线范围。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

### 工程师具体做了什么

- 【公开披露】既有记录的FDE依据是CEO访谈中描述工程师与业务、技术团队共同迭代。本轮访谈转录返回403，因此角色证据保留既有结论，不宣称重新听过或核过视频；官方PDF独立证明生产流程。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf) [来源3](https://metacast.app/podcast/tbpn/D9fOtj1E/alex-karp-live-from-aipcon-10-alex-karp-peter-zaffino-chad-wahlquist-sam-berry/eylg2ePA)

### 技术方案与数据流程

- 【公开披露】第116页将链路拆成三段：识别文档并抽取地址、被保险人和经纪人；融合内外部资料；按风险、利润、客户价值及成交倾向排序。列出的技术包括Claude 3.5、AIP、AWS Titan/Textract、Bedrock，以及Foundry/MuleSoft集成。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

- 【公开披露】第123页给出层次架构：数据本体/管道与管理，模型园地/编排/治理，AI应用服务，再到消费层；这是组件级架构，不是可直接复现的接口规格。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

- 【公开披露】第117—118页把提取、分析、综合摘要及风险重新排序放在人工之前；核保师分析AI输出后才报价、绑定、记账、出单。不能将摘要准备少于一天扩写为自动承保少于一天。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

- 【公开披露】第124页RAG示例先检索文档，找到财报后把上下文与指令送给模型，答案带页码，核保师确认或修正数值；它说明设计方式，不等于披露真实评测集或生产准确率。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

- 【分析／复现建议】复现建议，非客户已公开实现：按险种建立关键字段及证据页码验收集；把事实抽取、推断风险和商业排序分开评测，对无法定位原文的结论要求人工回看。

### 解决程度与业务提升

- 【公开披露】官方主张可在一天内完成送审资料准备，提升不增员情况下的容量；未给出人均产出变化或独立核保质量审计。投资者增长预测不能当成已经实现的项目收益。 [来源1](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)

### 尚未公开的信息

- 【未披露】未披露提示词、分块/检索/重排参数、各模型分工细节、训练/评测样本和逐险种失败率。

- 【未披露】未披露模型输出如何校验为结构化字段、跨来源冲突如何解决、人工拒绝率及生产回滚策略。

- 【未披露】未披露端到端核保周期、已实现净节省、整体实施维护费用及损失率变化；未将较新年度集团表现归因于此助手。

### 关键技能
- 保险文档抽取
- 来源追踪及证据链
- 结构化风险字段校验
- 人审队列与权限隔离

### 风险
- 摘要遗漏会影响承保；自动排序不得变成未经审核的最终决定
- 客户发言不是损失率改善的独立审计

### 限制
- 保险与银行按不同业务行业归类
- 不要从<1天资料整理扩写成全流程核保自动化
- 访谈是客户陈述；不是独立质量／损失率审计
- 3-4周对比仅本次见于转录而未在官方PDF直接核读，建议只写官方<1天

### 来源
1. [已生产、AI链路、人审、<1天](https://www.aig.com/content/dam/aig/america-canada/us/documents/investor-relations/aig_investor_day_2025__presentation.pdf)
2. [TBPN原始AIPCon10采访；本次直接打开失败](https://www.youtube.com/watch?v=72kQ7PYBaGk)
3. [客户原始访谈可读转录；时间与视频有约5分钟差](https://metacast.app/podcast/tbpn/D9fOtj1E/alex-karp-live-from-aipcon-10-alex-karp-peter-zaffino-chad-wahlquist-sam-berry/eylg2ePA)
4. [较新客户官方确认AI核心部署](https://www.aig.com/home/investor-relations/aig-2025-annual-report)
5. [AIG提交美国证券交易委员会的2025年报：总部](https://www.sec.gov/Archives/edgar/data/5272/000000527226000023/aig-20251231.htm)

## 39. Airbus A350生产：A350生产数据与质量协同

国家：法国；项目落地：法国
行业：航空航天制造
国家口径：本例为法国图卢兹A350工厂项目，亲历工程师明确说明在图卢兹驻厂。Airbus运营总部位于法国；母公司Airbus SE注册地在荷兰，不能将荷兰注册地误作本项目落地国。

概述：缺件、工单与质量信息分散，制造团队难以协调复杂装配。

流程：整合工单、缺件、质量不合格数据，提供任务状态、部件位置、排程与历史质量问题搜索，让制造团队协调A350增产。

落地程度：历史真实工厂生产部署；前FDE于2015加入，回忆在图卢兹工厂工作一年，每周四天。

人工职责：制造人员继续完成和勾选工单、查排程、处理质量问题；没有给出削减/保留人数。

证据说明：Nabeel Qureshi第一人称说明自己以 FDE（Forward Deployed Engineer，前线部署工程师）入职并在Airbus工厂每周驻场4天、持续约一年；官方另证实生产项目与结果。

可切入环节：从一个工位的缺件和未关闭质量问题视图切入，保留原系统的质量放行权。

- A350生产/交付节奏：加快33%（供应商口径）。口径：官网称A350生产增加33%；2022官方白皮书将指标标为A350交付加速33%。完整基准期、原始数量及计算方法未披露，不能自行换算为工时减少。

- 项目费用与净节省：未公开。口径：供应商较广Skywise平台的节约估计不能归入此2015 A350项目。

### 介入前的问题与基线

- 【公开披露】A350增产需协调分散的工单、缺件与质量不合格记录；白皮书把保持质量安全下扩产作为目标。它同时讨论后来的Skywise平台，需按项目和年代拆开阅读。 [来源1](https://nabeelqu.co/reflections-on-palantir) [来源4](https://www.palantir.com/assets/xrfr7uokpv1b/5plfYze5aVCisYHuvLhDZ2/c6713af4b4c5fff5a73b5e1683302898/Palantir_Operational_Complexity_Whitepaper_FINAL.pdf)

### 工程师具体做了什么

- 【公开披露】Nabeel Qureshi回忆2015年作为FDE加入后，在图卢兹工厂与制造人员每周共同工作四天，持续约一年；贡献是围绕现场流程构建运营软件，非部署现代生成式模型。 [来源1](https://nabeelqu.co/reflections-on-palantir)

### 技术方案与数据流程

- 【公开披露】把工单、缺件和不合格记录接入协作界面，工人可更新任务、查看其他团队进度、部件位置及排程；历史质量问题支持模糊/语义搜索，帮助查看过去如何处理。没有证据表明这里用了今天的大语言模型。 [来源1](https://nabeelqu.co/reflections-on-palantir)

- 【公开披露】官方白皮书补充排程、班次、部件、交付与缺陷的统一视图。其维护情景模拟、海量传感器及航空公司生态属于混合的Airbus/Skywise说明，不能全部倒灌为2015驻厂项目技术。 [来源4](https://www.palantir.com/assets/xrfr7uokpv1b/5plfYze5aVCisYHuvLhDZ2/c6713af4b4c5fff5a73b5e1683302898/Palantir_Operational_Complexity_Whitepaper_FINAL.pdf)

- 【分析／复现建议】复现建议，非客户已公开实现：保留工单系统及质量系统各自的权威状态，以统一飞机、工位、零件和不合格单标识建立关系；不要用协作界面的“已完成”替代质量签署。

- 【分析／复现建议】复现建议，非客户已公开实现：搜索历史处置需显示适用机型、零件版本、批准日期和责任人；语义相似只是候选线索，不能授权沿用不适用的维修或制造步骤。

### 解决程度与业务提升

- 【公开披露】白皮书将33%标为A350交付加速；亲历者另述制造速度约四倍，但缺少共同基准，二者不互相验证。17亿美元是Skywise平台年度估计节省，不能作为该A350项目ROI。 [来源1](https://nabeelqu.co/reflections-on-palantir) [来源4](https://www.palantir.com/assets/xrfr7uokpv1b/5plfYze5aVCisYHuvLhDZ2/c6713af4b4c5fff5a73b5e1683302898/Palantir_Operational_Complexity_Whitepaper_FINAL.pdf)

### 尚未公开的信息

- 【未披露】具体源系统名称、ETL/变更捕获方式、对象映射、搜索模型及准确率未披露。

- 【未披露】实际角色权限、回写冲突处理、停机降级、验收测试及质量放行门禁未披露；不得用平台一般功能补成客户已实施事实。

- 【未披露】33%的起止期、分母、原始交付数量及独立因果评估未给出；项目合同、驻场与长期维护总成本未公开。

### 关键技能
- 工单/物料主数据统一
- 数据质量与权限
- 制造流程和排程约束
- 让一线人员可操作的界面

### 风险
- 此为前生成式AI的数据工程案例，不应宣称LLM自动造飞机
- 作者披露持有Palantir股票；产量指标还有其他管理与产线因素

### 限制
- 前生成式AI的数据集成／运营软件案例，不能称LLM自动造飞机
- 亲历者披露持有PLTR股票；成效非独立审计
- A350生产项目与2017 Skywise平台以及2026同名公司改组分开
- 33%与4x基线不同，不互相验证
- 最后QA修正：17亿美元属于Skywise平台估计，不属于已确认2015 A350 FDE单项目节省。
- 官方另有Skywise平台年节约估计，范围不同，不作为本A350项目的成本成效。

### 来源
1. [亲历FDE身份、驻场方式、具体流程](https://nabeelqu.co/reflections-on-palantir)
2. [官方A350生产33%口径](https://www.palantir.com/offerings/supply-chain/)
3. [官方Airbus/Skywise合作历史](https://www.palantir.com/impact/airbus/)
4. [直接读取PDF；33%是A350交付加速，$1.7B是Skywise平台年估计节省（独立第三方估计），不能等同A350 FDE项目ROI](https://www.palantir.com/assets/xrfr7uokpv1b/5plfYze5aVCisYHuvLhDZ2/c6713af4b4c5fff5a73b5e1683302898/Palantir_Operational_Complexity_Whitepaper_FINAL.pdf)
5. [官方白皮书：区分A350交付与Skywise平台效益](https://www.palantir.com/assets/xrfr7uokpv1b/5plfYze5aVCisYHuvLhDZ2/c6713af4b4c5fff5a73b5e1683302898/Palantir_Operational_Complexity_Whitepaper_FINAL.pdf)
6. [Airbus官方：欧洲地点图区分注册地与总部](https://mediaassets.airbus.com/pm_38_780_780729-ey5ygljerc.pdf)

## 40. Composio：AI代理工具集成基础设施

国家：美国；项目落地：未披露
行业：AI开发工具与API集成基础设施
国家口径：Composio官方DPA确认主体Sampark Inc.为美国特拉华公司并列旧金山办公室；Plank项目落地国家未披露。

概述：连接器、边界场景和多客户需求造成设计、开发和验证吞吐瓶颈；Plank团队把Claude与真实UI测试纳入日常工作。

流程：Claude辅助开发与方案讨论，Claude Design推进界面；并行处理多个范围，以Chrome MCP驱动真实UI做端到端验证。

落地程度：完整案例称该方式已成为嵌入团队的日常交付流程；具体生产模块、客户覆盖和上线日期未披露。

人工职责：工程师操作并验证真实产品UI、复现问题；代码合并审批和逐次人工检查规则未披露。

证据说明：具名客户页明确FDE/QA；新增完整案例直接说明嵌入Plank团队的工作流、工具及前后周期。仍为供应商自报，未披露受控评测方法。

可切入环节：分析：用最小权限工具集成建立回归评测。

- 单项交付周期：3–4周 → 4–5天。口径：Plank完整案例自报；无样本、统计窗口、工作日定义和复杂度控制，不换算统一倍数。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】新连接器、边界情况及客户需求不断增加，设计、构建、验证吞吐成为瓶颈，单项交付原需3—4周。 [来源5](https://joinplank.com/cases/composio)

### 工程师具体做了什么

- 【公开披露】嵌入Composio的Plank团队把Claude纳入日常开发和方案讨论，用Claude Design推进界面概念，并行处理多个工作范围。客户页另明确FDE与QA服务身份。 [来源1](https://joinplank.com/customers/composio) [来源5](https://joinplank.com/cases/composio)

### 技术方案与数据流程

- 【公开披露】工程师将Claude与Chrome MCP结合，操作真实产品UI做端到端验证、复现问题；这是工程开发/质量流程，未披露Composio生产代理的基础模型或内部路由架构。 [来源5](https://joinplank.com/cases/composio)

- 【分析／复现建议】复现建议，非客户已公开实现：固定相同复杂度需求，分别记录设计、实现、测试、返工和人工审核时间；测试跨账号权限与工具版本变化，避免只比较最快任务。

### 解决程度与业务提升

- 【公开披露】供应商自报单项交付由3—4周缩至4—5天，并可并行多个范围；未给样本数、统计周期或任务复杂度控制。质量改善为定性描述，无缺陷率。 [来源5](https://joinplank.com/cases/composio)

### 尚未公开的信息

- 【未披露】Claude具体型号/版本、提示模板、并行机制、Chrome MCP配置、测试集、通过率与人工合并门禁未公开。

- 【未披露】交付周期所含工作日口径、样本量、成本账单、工程团队人数和净收益未公开。

### 关键技能
- 分析：工具接口契约测试
- 分析：用户授权隔离

### 风险
- 分析：工具权限扩散
- 分析：跨租户凭据泄露

### 限制
- 工程交付提速不等于Composio生产代理任务成功率或客户ROI提升。
- 周期为供应商自报，未给样本和可比性控制；融资与全平台规模不作为项目成果。

### 来源
1. [Composio × Plank](https://joinplank.com/customers/composio)
2. [Plank Customers](https://joinplank.com/customers)
3. [Composio Data Processing Addendum](https://composio.dev/legal/dpa)
4. [Composio product](https://composio.dev/)
5. [Composio × Plank：以Claude压缩交付周期](https://joinplank.com/cases/composio)

## 41. Kernel：代理云浏览器基础设施

国家：美国；项目落地：未披露
行业：AI云浏览器基础设施
国家口径：投资方Y Combinator公司页及创始人发布确认Kernel位于旧金山，country为美国；Plank交付覆盖国家未披露。

概述：Plank客户页将Kernel浏览器基础设施工作列为前线部署工程师（Forward Deployed Engineer）与Core AI。

流程：支持AI代理及网页自动化的浏览器基础设施；Plank具体模块与架构未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从受控测试网页与会话回放切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【分析／复现建议】浏览器代理需要把网页动作、会话状态与故障定位连起来；这是产品需求分析，未披露Plank介入前的具体故障或基线。

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · Core AI，工作主题为代理云浏览器基础设施；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/kernel)

### 技术方案与数据流程

- 【公开披露】客户产品背景：通过隔离的Chromium云浏览器让代理操作网站，并提供登录态管理、浏览器遥测、实时查看和MP4会话录制。该页未识别哪些组件由Plank实现。 [来源4](https://www.kernel.sh/)

- 【分析／复现建议】复现建议，非客户已公开实现：应分别回放导航、登录态过期、页面变化和超时场景，记录任务完成率、每步耗时和人工接管；登录凭据与录像应隔离。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】CDP/Playwright版本、浏览器隔离方案、Plank负责的模块、模型与并发配置、验收集和交付前后失败率未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：浏览器会话与并发管理
- 分析：隔离和可观测性

### 风险
- 分析：浏览器权限及登录态泄露
- 分析：网页内容诱导代理越权

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Kernel × Plank](https://joinplank.com/customers/kernel)
2. [Plank Customers](https://joinplank.com/customers)
3. [Kernel company profile](https://www.ycombinator.com/companies/kernel)
4. [Kernel product](https://www.kernel.sh/)

## 42. SardineAI：反欺诈与合规AI风险平台

国家：美国；项目落地：未披露
行业：金融反欺诈与合规软件
国家口径：Sardine官方隐私政策明确美国总部；政策中Shield的印度数据存储不等于Plank项目落地印度，故deploymentCountries留空。

概述：Plank客户页列明为SardineAI风险平台提供前线部署工程师（Forward Deployed Engineer）服务。

流程：工作范围为欺诈与合规AI风险平台；具体模型、决策阈值和系统集成未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：先做分析员只读辅助及历史回放评估。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【分析／复现建议】反欺诈需要在阻止损失与误伤正常交易之间权衡；原系统的误报、漏报、处理时长和具体改造起点未公开。

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE，工作主题为反欺诈与合规AI风险平台；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/sardineai)

### 技术方案与数据流程

- 【公开披露】客户产品背景：平台结合设备/行为信号、交易数据、规则和机器学习；Sardine Flow把数据、API、代理与人工审核串成工作流，案件管理供分析员调查和处置。不能据此认定Plank交付了Flow或任何指定模型。 [来源5](https://www.sardine.ai/)

- 【分析／复现建议】复现建议，非客户已公开实现：应按时间切分历史案件回放，分别测误报、漏报、调查时长及不同群体影响；高影响封禁或上报需明确人工权限与审计。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank涉及反欺诈还是AML模块、模型/规则阈值、特征来源、案件标注、线上审批与回滚、误报漏报变化未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：风险数据管道
- 分析：模型漂移和审计

### 风险
- 分析：误拦截正常交易
- 分析：敏感身份数据越权

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [SardineAI × Plank](https://joinplank.com/customers/sardineai)
2. [Plank Customers](https://joinplank.com/customers)
3. [Sardine Shield Privacy Policy](https://www.sardine.ai/shield/privacy)
4. [Sardine Notabene partnership](https://www.sardine.ai/press/pr/crypto-travel-rule-compliance)
5. [Sardine平台](https://www.sardine.ai/)

## 43. Diagon AI：工业设备智能采购搜索

国家：美国；项目落地：未披露
行业：工业设备采购平台
国家口径：Diagon官方隐私页明确US-based，官网链接的公司账号列旧金山总部；Plank实际项目国家未披露。

概述：Plank披露为Diagon AI设备寻源平台提供前线部署工程师（Forward Deployed Engineer）服务。

流程：工业设备、供应商及服务商搜索与比较；官网品牌为Albus，Plank具体实现边界未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：以带来源的设备规格检索和比较切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】客户官网将设备采购渠道分散、比较困难列为产品要解决的问题；未提供Plank介入前采购周期或人工工时。 [来源5](https://diagon.ai/)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE，工作主题为工业设备智能采购搜索；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/diagon-ai)

### 技术方案与数据流程

- 【公开披露】客户产品背景：现官网使用Albus品牌，用户输入设备型号、规格和预算，平台跨来源搜索并对照规格、价格和库存，用户再联系卖方询价购买。这是产品流程，不是Plank已披露的数据管道。 [来源5](https://diagon.ai/)

- 【分析／复现建议】复现建议，非客户已公开实现：应保留规格原文、单位、来源及抓取时间，分别测型号匹配和规格抽取；报价、库存和最终采购由采购人员验证。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】模型、搜索/排序与去重方法、设备数据许可、ERP连接、验收样例和采购周期/价格的可归因改善未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：产品规格结构化
- 分析：供应商数据检索

### 风险
- 分析：规格或库存过时
- 分析：高价值设备采购不应仅凭模型推荐

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Diagon AI × Plank](https://joinplank.com/customers/diagon-ai)
2. [Plank Customers](https://joinplank.com/customers)
3. [Diagon Privacy Policy](https://diagon.ai/privacy-policy)
4. [Diagon official LinkedIn](https://www.linkedin.com/company/diagon-tech/)
5. [Diagon／Albus设备采购产品](https://diagon.ai/)

## 44. Artyc：温控运输物联网冷链系统

国家：美国；项目落地：未披露
行业：医疗与生命科学冷链物流设备
国家口径：Artyc官方公司账号列美国旧金山总部；未据其国际运输宣传推断Plank项目国家。

概述：Plank客户页明确Artyc温控运输物联网工作使用前线部署工程师（Forward Deployed Engineer）及QA服务。

流程：面向温度敏感货物的IoT冷链物流；未披露Plank负责传感器、云端还是应用侧，也未公开AI具体用途。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从温度记录一致性和异常告警验证切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】客户产品面向冷链包装、干冰采购、温度异常报告及运输可见性问题；Plank介入前损耗率、告警及时性和人工工时未公开。 [来源4](https://www.shipartyc.com/)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · QA，工作主题为温控运输物联网冷链系统；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/artyc)

### 技术方案与数据流程

- 【公开披露】客户产品背景：可充电复用运输箱配合云平台，自动上传GPS、温度、开盖和冲击事件，触发温度/低电量/开盖告警并保留运输日志。不能将设备、固件或云平台全部归为Plank成果。 [来源4](https://www.shipartyc.com/)

- 【分析／复现建议】复现建议，非客户已公开实现：应模拟断网、断电、传感器漂移及迟到事件，以校准温度仪比对；异常处置需由操作人员确认，不能让预测替代实测温控。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank负责设备/固件/云端/应用的边界、是否实际使用AI、传感器协议、告警规则、温控验证、货损与成本前后数据未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：传感器遥测校验
- 分析：离线与断电场景测试

### 风险
- 分析：温控失效导致货物损毁
- 分析：运输日志与实际温度不一致

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Artyc × Plank](https://joinplank.com/customers/artyc)
2. [Plank Customers](https://joinplank.com/customers)
3. [Artyc official company profile](https://www.linkedin.com/company/artycpbc/)
4. [Artyc products](https://www.shipartyc.com/)

## 45. Retail Development Partners：零售门店扩张分析模型

国家：美国；项目落地：未披露
行业：零售地产选址与门店扩张分析
国家口径：RDP官方公司账号明确总部洛杉矶，美国；Plank页提到品牌但未列具体门店或国家，不据品牌全球运营推断落地国家。

概述：Plank明确为RDP定制扩张模型，服务类型前线部署工程师（Forward Deployed Engineer）与Core AI。

流程：以零售门店拓展为工作范围；RDP官网说明结合门店数据及出行模式分析商圈、空白市场与组合表现，Plank具体数据与实现未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从历史门店回测与可解释商圈分析切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【未披露】公开页没有Plank介入前选址方法、人工步骤、历史门店样本或预测误差基线。

### 工程师具体做了什么

- 【公开披露】客户页标注FDE与Core AI，主题为为McDonald’s、Sweetgreen、Chipotle等品牌定制扩张模型；未逐品牌披露项目范围。 [来源1](https://joinplank.com/customers/retail-development-partners)

### 技术方案与数据流程

- 【分析／复现建议】复现建议，非客户已公开实现：把历史门店、销售、商圈、竞争点和租金按时间和地理区域拆分训练/验证，防止相邻店和未来销量泄漏；交由地产团队审查候选地及假设。

### 解决程度与业务提升

- 【未披露】没有选址准确率、开店数、销售提升或资本回报的项目级量化数据。

### 尚未公开的信息

- 【未披露】数据供应商和许可、地理特征、模型类型、预测目标、回测方法、决策审批、上线范围及成本均未公开。

### 关键技能
- 分析：地理空间特征工程
- 分析：选址预测回测

### 风险
- 分析：出行数据代表性偏差
- 分析：预测误差可能放大地产资本损失

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Retail Development Partners × Plank](https://joinplank.com/customers/retail-development-partners)
2. [Plank Customers](https://joinplank.com/customers)
3. [Retail Development Partners official profile](https://www.linkedin.com/company/retail-development-partners)
4. [Retail Development Partners platform](https://www.retaildevelopmentpartners.com/)

## 46. MintMCP：企业MCP工具网关

国家：美国；项目落地：未披露
行业：企业AI工具接入与安全基础设施
国家口径：官方条款列美国加州主体地址；MintMCP产品已改称Mintive，保留供应商案例原名称；项目国家未披露。

概述：Plank客户页明确企业MCP网关为前线部署工程师（Forward Deployed Engineer）服务范围。

流程：支持企业AI代理通过MCP接入工具；具体部署架构、工具清单与供应商交付接口未公开。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从只读工具网关和调用审计切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】客户产品要解决未管理MCP连接、过度授权和凭据风险；未披露Plank项目开始时的连接数量、事故或人工维护负担。 [来源4](https://www.mintmcp.com/)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE，工作主题为企业MCP工具网关；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/mintmcp)

### 技术方案与数据流程

- 【公开披露】客户产品背景：MintMCP现名Mintive；网关按角色提供已批准工具，工具级开关可禁用破坏性动作；每个代理独立凭据，调用关联身份并可导出审计日志。未证明这些控制均由Plank设计或在本项目启用。 [来源4](https://www.mintmcp.com/)

- 【分析／复现建议】复现建议，非客户已公开实现：应建立工具白名单，区分读写权限，测试撤销身份后访问是否立即失效；用越权和提示注入样例验证并保存审计证据。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank具体连接器、网关部署位置、模型、鉴权实现、权限矩阵、提示注入测试结果、企业上线数量及费用未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：MCP权限与租户隔离
- 分析：工具调用审计

### 风险
- 分析：工具权限滥用
- 分析：提示注入诱发数据外泄

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [MintMCP × Plank](https://joinplank.com/customers/mintmcp)
2. [Plank Customers](https://joinplank.com/customers)
3. [MintMCP Terms of Service](https://www.mintmcp.com/terms)
4. [MintMCP product](https://www.mintmcp.com/)

## 47. Vendora：杂货零售数字商务平台

国家：美国；项目落地：未披露
行业：杂货零售POS与电商软件
国家口径：Y Combinator投资方公司页列纽约总部，美国；未将其美国行业市场规模当作Plank项目部署国家。

概述：Plank为杂货商垂直SaaS商业平台提供前线部署工程师（Forward Deployed Engineer）与QA服务。

流程：服务范围为杂货商数字商务；客户官方创始人介绍包括既有系统数据接入与商品数据增强，但Plank具体负责模块未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从商品数据质量与只读库存校验切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】创始人称杂货行业依赖过时系统和人工流程，商家缺少经营线上渠道的工具；这是行业/产品起点，不是Plank项目前后对照实验。 [来源3](https://www.ycombinator.com/companies/vendora)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · QA，工作主题为杂货零售数字商务平台；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/vendora)

### 技术方案与数据流程

- 【公开披露】客户创始人说明产品接入零售商既有系统、摄取数据，经AI工作流增强后形成第三方数据feed，同时提供自有网站/应用门店。未披露Plank负责哪条feed、哪个POS接口或AI环节。 [来源3](https://www.ycombinator.com/companies/vendora)

- 【分析／复现建议】复现建议，非客户已公开实现：应对商品SKU、单位、价格、税、库存建立统一映射，测试重复事件、缺货和价格冲突；先只读对账再开放订单写入。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】具体POS/支付商、模型与数据增强方法、同步频率、订单幂等、人工改价机制、验收数据和项目级营收或节省未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：商品目录标准化
- 分析：库存与订单一致性

### 风险
- 分析：库存或价格同步错误
- 分析：支付与订单重复写入

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Vendora × Plank](https://joinplank.com/customers/vendora)
2. [Plank Customers](https://joinplank.com/customers)
3. [Vendora YC company and founder launch](https://www.ycombinator.com/companies/vendora)
4. [Vendora products](https://www.vendora.io/)

## 48. SMI Aware：社交媒体电子取证引擎

国家：美国；项目落地：未披露
行业：诉讼支持与电子证据发现服务
国家口径：客户官方Solutions页列美国宾夕法尼亚匹兹堡地址；Plank交付实际覆盖国家未披露。

概述：Plank客户页明确为SMI提供前线部署工程师（Forward Deployed Engineer）及QA，范围为可供法律审查的社交媒体发现引擎。

流程：电子发现与证据保存系统；客户产品包含专业分析员审核、来源保存和报告，Plank具体模块未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：限定案件范围，先构建可追溯检索与人工复核。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】客户指出非正式搜索和截图可能误认身份、脱离上下文或无法事后认证；本次Plank项目原始召回率、证据保全缺口和处理时间未披露。 [来源4](https://smiaware.com/)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · QA，工作主题为社交媒体电子取证引擎；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/smi)

### 技术方案与数据流程

- 【公开披露】客户产品背景：公开网络活动经专业分析员审核，保留来源、上下文和方法，形成可审查报告；产品提供案件工作流API。人工审核是客户整体服务承诺，未证实Plank设计的审核界面或门禁。 [来源4](https://smiaware.com/)

- 【分析／复现建议】复现建议，非客户已公开实现：应先限定合法案件范围，建立身份消歧与来源保全链；模型发现须经分析员核实，避免同名误匹配和无关个人数据过采集。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank交付的采集/检索/报告模块、AI模型、平台访问方式、证据哈希与保留策略、准确率、分析员复核工作量及成本未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：证据来源与保全链
- 分析：检索范围和身份消歧

### 风险
- 分析：误认同名人员
- 分析：无关私人信息过度采集

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [SMI Aware × Plank](https://joinplank.com/customers/smi)
2. [Plank Customers](https://joinplank.com/customers)
3. [SMI Aware solutions](https://smiaware.com/solutions/)
4. [SMI Aware产品与分析员流程](https://smiaware.com/)

## 49. Cheiron：生物制药研发AI工作层

国家：美国；项目落地：未披露
行业：生物制药研发情报软件
国家口径：Cheiron官方公司账号列总部美国Los Altos，并另列韩国办公室；韩国办公存在不能证明本项目在韩国部署，实际项目国家留空。

概述：Plank客户页明确生物制药药物项目AI工作层提供前线部署工程师（Forward Deployed Engineer）及Core AI服务。

流程：工作范围是药物研发AI系统；客户介绍其跨文献、临床与法规证据的工作流，Plank实现边界未披露。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从有出处的文献筛选和证据表整理切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【分析／复现建议】药物项目需要整合可追溯科学与法规证据；具体客户团队原工作流、瓶颈和基线未公开。

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · Core AI，工作主题为生物制药研发AI工作层；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/cheiron)

### 技术方案与数据流程

- 【公开披露】客户官网可读取正文仅说明药物研发、临床研究、法规与医学事务工作流，以及带证据链接的可验证输出；没有足够材料重建检索架构，更不能归因给Plank。 [来源4](https://www.cheiron.bio/)

- 【分析／复现建议】复现建议，非客户已公开实现：应以有版本与日期的文献和法规构建评测，检查引用是否真正支持结论；研究员复核证据表，保留不确定性和相反结果。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】基础模型、文献/临床/法规数据源、检索/重排/知识图谱、权限、专家评测、引用正确率、研发周期及费用未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：科学证据溯源
- 分析：领域知识评测

### 风险
- 分析：过时或错误研究结论
- 分析：不能把研发辅助输出当临床建议

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Cheiron × Plank](https://joinplank.com/customers/cheiron)
2. [Plank Customers](https://joinplank.com/customers)
3. [Cheiron official company profile](https://www.linkedin.com/company/cheiron-bio)
4. [Cheiron product](https://www.cheiron.bio/)

## 50. Jolly：一线员工激励与企业系统集成

国家：美国；项目落地：未披露
行业：一线员工绩效激励软件
国家口径：Jolly官方公司账号明确美国纽约总部；个案没有逐一说明部署国家，故deploymentCountries为空。

概述：激励数据分散在医疗记录和内部管理系统，运营需要跨系统核对。

流程：接入EMR与HRIS，映射客户数据结构，汇总招聘/留任等指标，连接积分账本及钱包；配置可排障和对账的管理员界面。

落地程度：官方列Team Select Home Care、Visiting Angels、Dunkin和Coinbase为部署示例；作为一项Jolly工程交付合并记录。

人工职责：管理员处理日常运营、排障与数据核对；人员激励审批及逐条审核规则未知。

证据说明：具名客户页有独立前线部署工程师（Forward Deployed Engineer）段，明确30+ EMR、客户内部IT系统集成、定制管理仪表盘，并列实际企业部署；QA段记录上线工单、版本缺陷和修复。

可切入环节：分析：从只读对账和人工确认的积分计算切入。

- EMR集成覆盖：30多个。口径：供应商自报接口系统数量；不是30家终端客户或模型性能。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【分析／复现建议】从已披露交付可推知，客户EMR/HRIS及内部仪表盘模式各异，需要整合激励与推荐数据并支持日常对账；原先人工耗时与错误率未给出。 [来源1](https://joinplank.com/customers/jolly)

### 工程师具体做了什么

- 【公开披露】FDE对接30多个EMR，采用API、浏览器抓取、RPA和直接数据库接入；建设管理员排障/对账界面，对接内部管理仪表盘、积分账本与web3钱包，并映射认证流程。 [来源1](https://joinplank.com/customers/jolly)

- 【公开披露】QA团队梳理需求与初始部署测试，制作数据转换工具，关联发布与客户故障并修复；制定HRIS集成路线，将客户模式映射到统一产品模式。 [来源1](https://joinplank.com/customers/jolly)

### 技术方案与数据流程

- 【公开披露】数据由客户系统进入统一模式，激励/推荐数据汇总为招聘、留任和资源配置指标；管理员可日常操作、排障和核对。公开的是集成与控制点，未给模型或实时流水线拓扑。 [来源1](https://joinplank.com/customers/jolly)

- 【分析／复现建议】复现建议，非客户已公开实现：为每个来源设置字段契约与对账，测试重复/迟到事件、失效登录和模式变化；积分及钱包写入应有幂等键、审批和可追溯撤销。

### 解决程度与业务提升

- 【公开披露】列出Team Select Home Care、Visiting Angels、Dunkin及Coinbase部署示例，并报告30+ EMR连接；管理员界面减少客服工单为定性描述，无降幅。员工规模不是实际使用人数。 [来源1](https://joinplank.com/customers/jolly)

### 尚未公开的信息

- 【未披露】AI是否参与积分/激励判断、基础模型、30+ EMR清单、数据刷新周期、测试通过率、权限与付款批准链未公开。

- 【未披露】部署日期和国家、工单前后数量、留任/招聘的可归因变化、实施与运行成本、净收益未公开。

### 关键技能
- 分析：HRIS/EMR模式映射
- 分析：账本与数据对账

### 风险
- 分析：错误积分影响员工报酬
- 分析：医疗与员工数据权限边界

### 限制
- 未将每个终端客户拆为一例；客户员工规模不是实际系统使用人数。
- 未披露AI在激励系统中具体模型与决策边界。

### 来源
1. [Jolly × Plank](https://joinplank.com/customers/jolly)
2. [Jolly official company profile](https://www.linkedin.com/company/jolly/)

## 51. NEAR AI：代理基础设施与开源安全

国家：美国；项目落地：未披露
行业：隐私保护AI与代理基础设施
国家口径：官方隐私政策确认主体Jasnah Inc.注册于美国特拉华州；不是用NEAR基金会所在地推断。Plank项目国家未披露。

概述：Plank将NEAR AI代理基础设施和开源安全列为前线部署工程师（Forward Deployed Engineer）与Core AI服务。

流程：公开工作范围为代理基础设施与开源安全；具体安全组件、部署拓扑和交付清单未知。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从可复现的隔离测试与依赖风险检查切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【分析／复现建议】代理基础设施及开源安全是Plank披露的工作主题；未说明介入前的安全缺陷、推理瓶颈或业务损失。

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为Core AI · FDE，工作主题为代理基础设施与开源安全；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/near-ai)

### 技术方案与数据流程

- 【公开披露】客户当前产品背景：NEAR AI Cloud以Intel TDX和NVIDIA机密计算硬件运行开放权重模型，响应附证明，并提供OpenAI兼容接口。当前产品页不证明Plank交付TEE、证明验证器或其中某一模型。 [来源4](https://near.ai/)

- 【分析／复现建议】复现建议，非客户已公开实现：应把代码依赖、构建产物、运行镜像与证明验证分开检查，测试证明无效时拒绝响应；安全与隐私收益需要威胁模型验证。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank负责仓库/安全组件、具体模型和版本、是否涉及TEE服务、威胁模型、审计范围、修复漏洞数量及性能/成本变化未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：开源依赖审计
- 分析：代理执行隔离

### 风险
- 分析：隐私承诺与实际数据流不一致
- 分析：供应链漏洞

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [NEAR AI × Plank](https://joinplank.com/customers/near-ai)
2. [Plank Customers](https://joinplank.com/customers)
3. [NEAR AI Privacy Policy](https://near.ai/privacy-policy)
4. [NEAR AI私有推理产品](https://near.ai/)

## 52. Rye Worldwide：代理电商统一结账API

国家：美国；项目落地：未披露
行业：电商结账与代理交易基础设施
国家口径：Rye官方隐私政策列美国办公与特拉华州主体地址。Rye于2026年被Jolly宣布收购；此例是独立具名结账API工作，与Jolly EMR/激励集成范围不同。项目落地国家未披露。

概述：Plank客户页将Rye统一结账API列为前线部署工程师（Forward Deployed Engineer）与Core AI服务。

流程：工作范围为代理电商统一结账接口；Plank负责的商户集成、付款授权和重试机制细节未公开。

落地程度：供应商列为具名前线部署工程师（Forward Deployed Engineer）服务客户；该项目处于试点还是全面生产、上线日期与规模均未单独披露，阶段未知。

人工职责：具体人审流程、人工接管及审批比例未公开。

证据说明：供应商具名个案页将服务明确标为前线部署工程师（Forward Deployed Engineer），并列客户业务范围；结合客户主体资料，按B级组合收录。个案工程分工、具体上线阶段和实际成效披露有限，不能从网站总体描述推定本项目已规模生产。

可切入环节：分析：从沙盒商户、明确确认和可回滚订单测试切入。

- 项目量化成效：未公开。口径：未披露Plank工程贡献对应的上线周期、使用规模或效果指标；不将客户融资额当项目结果。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】客户官网将代理能推荐商品但难完成结账描述为产品问题；Plank项目前结账成功率与具体商户故障未公开。 [来源5](https://rye.com/)

### 工程师具体做了什么

- 【公开披露】Plank具名客户页标注服务为FDE · Core AI，工作主题为代理电商统一结账API；没有逐项工程交付、人员分工或可验证上线记录。 [来源1](https://joinplank.com/customers/rye-worldwide)

### 技术方案与数据流程

- 【公开披露】客户产品背景：输入商品URL和支付令牌，获取含税运总价并完成订单；平台称结合AI浏览器自动化与成功路径的确定性流程缓存，支付只用令牌。未证实缓存或支付实现由Plank交付。 [来源5](https://rye.com/)

- 【分析／复现建议】复现建议，非客户已公开实现：应以沙盒订单验证报价变化、库存耗尽、重复提交和超时重试；最终购买需明确授权，订单号与付款结果逐笔对账。

### 解决程度与业务提升

- 【未披露】未披露可归因于Plank的前后量化成效；客户产品规模、产品性能宣传、融资与其其他客户业绩均不作为本项目结果。

### 尚未公开的信息

- 【未披露】Plank负责商户、浏览器模型、缓存和失败回退、支付授权与幂等、项目测试样本、成功率前后变化和合同费用未公开。

- 【未披露】项目启动/上线日期、实施团队人数、部署国家、完整实施和运维费用及净ROI未公开。

### 关键技能
- 分析：交易幂等与订单对账
- 分析：支付权限边界

### 风险
- 分析：重复下单或误购
- 分析：支付资料泄露

### 限制
- 证据满足具名前线部署工程师（Forward Deployed Engineer）服务门槛，但案例披露较薄；客户产品能力不能全部归因于Plank。
- 未将公司总融资、全平台规模或其他供应商业绩作为本项目成效。

### 来源
1. [Rye Worldwide × Plank](https://joinplank.com/customers/rye-worldwide)
2. [Plank Customers](https://joinplank.com/customers)
3. [Rye Privacy Policy](https://rye.com/privacy-policy)
4. [Jolly official company announcement](https://www.linkedin.com/company/jolly/)
5. [Rye通用结账API产品](https://rye.com/)

## 53. OpenEvidence：OpenEvidence临床文献检索推理平台

国家：美国；项目落地：美国
行业：医疗信息检索与临床知识软件
国家口径：主体美国：OpenEvidence一手诉状第23段确认美国注册及主要营业地；部署范围美国来自Baseten案例Results每州医生使用的描述，指服务用户覆盖，不代表GPU驻留地。其他国家未列出。

概述：临床人员检索医学文献时需要低延迟、可靠的模型服务。

流程：前线部署工程师（Forward Deployed Engineer）与性能工程师共同优化嵌入模型、多云扩容和客户端瓶颈，简化模型部署与监控。

落地程度：已生产服务；案例报告美国医生实际使用，Baseten每周处理数十亿推理请求。后者是底层模型调用量，不是医生人数或独立问诊次数。

人工职责：OpenEvidence工程团队控制模型和应用；临床人员自行判断信息，未披露逐回答人工复核机制。

证据说明：Baseten官方客户案例Solutions直接称前线部署团队与模型性能团队作为OpenEvidence工程团队的延伸，优化多云容量、嵌入推理、观测和部署；不是由供应商导航栏推断前线部署工程师（Forward Deployed Engineer）。

可切入环节：分析建议：先选非患者特定的文献检索任务，评测引用正确性并保留医生最终判断。

- 端到端延迟：超过700毫秒降至160毫秒。口径：官方案例报告降低78%；未给测量样本和分位数。

- 部署效率：6倍。口径：从多名工程师数小时改为一名工程师不到一小时；自报流程比较。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】原先自建推理；增长后基础设施管理挤占医疗产品研发时间，流量尖峰、硬件故障和GPU长期合约均构成约束。 [来源1](https://www.baseten.co/resources/customers/openevidence-delivers-instant-medical-information-with-baseten/)

### 工程师具体做了什么

- 【公开披露】前线部署及模型性能团队作为客户工程团队延伸，联合优化负载、引入BEI和Performance Client、配置多云容量，并协助接入训练基础设施。 [来源1](https://www.baseten.co/resources/customers/openevidence-delivers-instant-medical-information-with-baseten/)

### 技术方案与数据流程

- 【公开披露】项目明确使用BEI优化嵌入推理，Performance Client处理客户端吞吐瓶颈；MCM跨云、跨区域调度并提供按需冗余。未公布医疗检索数据库、召回与答案生成之间的完整接口。 [来源1](https://www.baseten.co/resources/customers/openevidence-delivers-instant-medical-information-with-baseten/)

- 【公开披露】技术背景：BEI的数据流为Rust前端→多核分词→按token上限打包并保持请求顺序→TensorRT-LLM C++推理→数值输出；批量语料摄取与低延迟在线查询需分别测试。 [来源3](https://www.baseten.co/blog/how-we-built-bei-high-throughput-embedding-inference/)

- 【公开披露】技术背景：BEI用启动时预分配内存、队列背压和扩容避免长请求引发OOM；FP8基准的余弦相似度不等于临床准确率，也不能据此断定本项目使用同一模型或量化。 [来源3](https://www.baseten.co/blog/how-we-built-bei-high-throughput-embedding-inference/)

- 【分析／复现建议】复现建议，非已公开实施：用相同医学查询验证召回、引用和答案一致性，另测峰值并发下端到端延迟；医生保留医疗判断，不把服务加速解释成临床验证。

### 解决程度与业务提升

- 【公开披露】端到端延迟由超过700毫秒降至160毫秒（约78%）；部署流程快6倍，基础设施维护工时减少8倍以上。案例称每周承载数十亿请求；无合同价或完整净成本数据。 [来源1](https://www.baseten.co/resources/customers/openevidence-delivers-instant-medical-information-with-baseten/)

### 尚未公开的信息

- 【未披露】模型名称、权重版本、向量库、切片和重排规则、各阶段时间占比未披露。

- 【未披露】未公开医学评测集、错误率、医生复核流程、患者数据权限与保留配置。

- 【未披露】部署6倍与维护8倍的样本、观察期及工程师工时原始记录未公开；没有可归因临床结局。

### 关键技能
- 分析：嵌入模型推理优化
- 分析：峰值容量与多云故障切换
- 分析：临床知识时效验证

### 风险
- 分析：低延迟不等于临床正确性
- 分析：医疗数据隐私
- 分析：高峰故障及引用错误

### 限制
- 效益为供应商与客户自报，没有独立对照。
- 本例是医学信息平台的推理基础设施，不是自动诊疗或临床效果验证。

### 来源
1. [OpenEvidence delivers instant, accurate medical information with the Baseten Inference Stack](https://www.baseten.co/resources/customers/openevidence-delivers-instant-medical-information-with-baseten/)
2. [OpenEvidence一手法院诉状](https://assets.alm.com/bd/d8/7ef64dac44bc9651ba27df49284a/openevidence-v-doximity-et-al-d-mass-25-cv-11802-dckt-000001-000-filed-2025-06-20-1.pdf)
3. [BEI技术深解](https://www.baseten.co/blog/how-we-built-bei-high-throughput-embedding-inference/)

## 54. Rime：Rime实时语音合成API上线与扩容

国家：美国；项目落地：未披露
行业：语音合成模型与开发者API
国家口径：主体国家为美国；来源：Baseten Rime官方客户故事，Company overview明确Based in San Francisco。项目实际落地国家未单独披露，不以总部推断。

概述：Rime需要将自研语音模型变成满足实时对话延迟的企业API。

流程：前线部署工程师（Forward Deployed Engineer）陪同API从模型到上市，优化跨区域路由、CPU/GPU分工、批处理和音频负载，并支持弹性GPU与观测。

落地程度：生产API；案例包含2024年可用性观察。

人工职责：Rime持续训练模型并运营API，Baseten参与基础设施交付；未披露逐音频人工审核。

证据说明：Rime CEO Lily Clifford在客户故事Solution直接说明Baseten前线部署工程师贯穿API上市全过程并解决关键基础设施问题；邻近段落详述多区域模型服务。

可切入环节：分析建议：先在授权声音和有限语言上上线API，逐语言测尾延迟与发音错误。

- p99响应延迟：不高于300毫秒。口径：Results称持续达到或优于客户SLA；不是整段语音生成完毕时间。

- 可用性：2024年100%。口径：CEO回顾2024年观察值，非未来永不故障保证。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】Rime已有自训语音合成模型，但需建立企业API；模型计算可达目标，跨地域网络与多MB音频响应却威胁p99小于300毫秒的SLA。 [来源1](https://www.baseten.co/resources/customers/rime/)

### 工程师具体做了什么

- 【公开披露】客户CEO明确称FDE全程协助API上市，处理基础设施问题；团队共同优化区域部署、批处理、CPU/GPU分工及响应载荷。 [来源1](https://www.baseten.co/resources/customers/rime/)

### 技术方案与数据流程

- 【公开披露】数据流是企业文本请求→地理邻近数据中心→自训TTS模型→音频响应；从T4迁移A10G以改善延迟与规模吞吐，L4和分数H100仅为文中试验方向。 [来源1](https://www.baseten.co/resources/customers/rime/)

- 【公开披露】Rime将推理指标接入Grafana，和其他关键服务统一监控。相关官方技术文说明可导出请求状态、端到端响应时间、副本及硬件使用率，通过OpenTelemetry/Prometheus抓取；通用60秒建议不是已披露Rime配置。 [来源3](https://www.baseten.co/blog/export-model-inference-metrics-to-observability-tools/)

- 【分析／复现建议】复现建议，非客户已披露：按地区、音频长度和并发测p50/p99，并拆开网络传输、排队、模型生成耗时；以真实声音样例做听感/发音回归，不能以延迟代替音质。

### 解决程度与业务提升

- 【公开披露】达到企业p99 300毫秒SLA，p50低于150毫秒；客户引语明确称2024年100%在线率。支持企业客户及按需GPU，但未披露账单节省与合同金额。 [来源1](https://www.baseten.co/resources/customers/rime/)

### 尚未公开的信息

- 【未披露】自训TTS架构、参数量、训练语料、音频编码与流式协议未披露。

- 【未披露】未披露音质评测集、人工审核和声音授权流程；200余声音是产品范围，不是本次FDE新增数。

- 【未披露】区域名单、副本数、负载实验规模、SLA统计口径和总拥有成本未披露。

### 关键技能
- 分析：流式音频与网络优化
- 分析：多区域低延迟部署
- 分析：GPU容量和SLA监控

### 风险
- 分析：声音授权与冒用
- 分析：跨地区音频数据保护
- 分析：历史可用性过度外推

### 限制
- 性能与可靠性为客户自报。
- 来源未披露具体地区或国家；多区域不能推断为指定国家部署。

### 来源
1. [How Rime.ai achieved state-of-the-art p99 latencies on Baseten](https://www.baseten.co/resources/customers/rime/)
2. [Baseten Rime官方客户故事](https://www.baseten.co/resources/customers/rime/)
3. [推理指标导出与Rime Grafana集成](https://www.baseten.co/blog/export-model-inference-metrics-to-observability-tools/)

## 55. Notion：Notion AI Meeting Notes语音转写管道

国家：美国；项目落地：未披露
行业：协作办公与知识管理软件
国家口径：主体国家为美国；来源：Notion官方：Making the Brand at Make with Notion，正文称San Francisco为home base，并描述从总部搬运家具。项目实际落地国家未单独披露，不以总部推断。

概述：会议笔记需要带说话人标签的快速转写与稳定生产管道。

流程：Matte Lim参与从零构建转写、说话人分离和多传输编排，再与Baseten模型、运行时、观测和网络团队一起生产化。

落地程度：已生产；供应商和参与工程师均确认AI Meeting Notes运行于Baseten。

人工职责：会议参加者查看和使用笔记；公开材料未披露逐篇人工审核。

证据说明：B组合：Baseten官方作者页把Matte Lim列为Forward Deployed Engineer；他本人公开说明参与Notion AI Meeting Notes从零构建及生产化，供应商官方客户页对应同一产品。不是把Notion一般客户身份当作前线部署工程师（Forward Deployed Engineer）。

可切入环节：分析建议：先在已获参与者同意的内部会议测试转写与说话人归属，允许用户纠正。

- 延迟改善：2–3倍。口径：官方客户视频标题所称lower latency，未提供绝对基线、分位数或采样方法。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】工程师描述为从0到1构建AI Meeting Notes；既有产品的人工记笔记耗时、旧系统模型和延迟绝对值没有公开。 [来源1](https://www.linkedin.com/posts/mattelim_one-of-the-highlights-of-my-first-year-at-activity-7504236590869782529-9_p8)

### 工程师具体做了什么

- 【公开披露】Matte Lim原帖自述参与Notion转录、说话人分离和多传输编排，并与模型、运行时、可观测性、计算及网络团队协作；官方作者页确认其FDE身份。 [来源1](https://www.linkedin.com/posts/mattelim_one-of-the-highlights-of-my-first-year-at-activity-7504236590869782529-9_p8) [来源2](https://www.baseten.co/author/matte-lim/)

### 技术方案与数据流程

- 【公开披露】产品层数据流：设备音频→分包处理商实时转录→带说话人信息的文本→结合用户笔记生成摘要/行动项。Notion列Baseten等多家处理商，未逐阶段指定供应商或模型。 [来源6](https://www.notion.com/help/ai-meeting-notes)

- 【公开披露】产品人工控制：用户取得参会者同意后启动/停止；摘要引用可跳回转录文本，用户控制分享，笔记继承页面权限。工作区管理员可关闭功能、配置转录删除。以上为Notion产品机制，非FDE交付清单。 [来源6](https://www.notion.com/help/ai-meeting-notes)

- 【公开披露】相关技术背景：pyannote按声学做说话人分离；Baseten文章讲分段/嵌入批调度、减少CPU-GPU搬运、索引微聚类和分阶段混合精度，并用DER评测。9.6倍和3.2倍是该文基准，不是Notion结果。 [来源5](https://www.baseten.co/blog/how-baseten-makes-pyannotes-diarization-models-96x-faster/)

- 【分析／复现建议】复现建议，非项目事实：分别验收转录WER、说话人DER、重叠说话、长音频和断网重试；跨设备音源能力不同，需要端到端测试而非只跑ASR模型。

### 解决程度与业务提升

- 【公开披露】Baseten案例页标题称延迟降低2—3倍；页面可读取内容未提供基准和绝对值。工程师的1→P99.99措辞仅指生产化努力，不能当99.99% uptime测量值。 [来源1](https://www.linkedin.com/posts/mattelim_one-of-the-highlights-of-my-first-year-at-activity-7504236590869782529-9_p8) [来源3](https://www.baseten.co/resources/customers/how-notion-acheived-2-3x-lower-latency-with-ai-meeting-notes/)

### 尚未公开的信息

- 【未披露】官方案例页正文为媒体形式，本次未取得可验证媒体转录；不能声称已审阅视频全部技术细节。

- 【未披露】实际ASR/diarization模型版本、传输协议、GPU配置、基准负载、质量指标未披露。

- 【未披露】项目费用、每分钟成本、绝对延迟及节省人力的数值未披露。

### 关键技能
- 分析：语音转写和说话人分离
- 分析：跨传输协议编排
- 分析：生产可观测性与音频质量评估

### 风险
- 分析：录音同意与会议隐私
- 分析：说话人归属错误
- 分析：摘要遗漏关键限定

### 限制
- 角色和项目来自两份一手材料组合，故B而非直接同页A。
- 本人提到的P99.99为生产化表达，未把它擅自解释为已验证可用性指标。
- 本轮完整读取工程师原帖与Notion产品帮助；Baseten客户页仅标题及媒体，未取得媒体转录。通用pyannote优化不能视为Notion已部署配置。

### 来源
1. [Building AI Meeting Notes with Notion at Baseten — Matte Lim](https://www.linkedin.com/posts/mattelim_one-of-the-highlights-of-my-first-year-at-activity-7504236590869782529-9_p8)
2. [Matte Lim — Forward Deployed Engineer](https://www.baseten.co/author/matte-lim/)
3. [How Notion achieved 2-3x lower latency with AI Meeting Notes](https://www.baseten.co/resources/customers/how-notion-acheived-2-3x-lower-latency-with-ai-meeting-notes/)
4. [Notion官方：Making the Brand at Make with Notion](https://www.notion.com/ja/blog/making-the-brand)
5. [说话人分离优化技术说明](https://www.baseten.co/blog/how-baseten-makes-pyannotes-diarization-models-96x-faster/)
6. [Notion AI Meeting Notes产品与隐私说明](https://www.notion.com/help/ai-meeting-notes)

## 56. Scaled Cognition：Scaled Cognition APT代理模型混合云上线

国家：美国；项目落地：未披露
行业：企业客服代理模型与智能体平台
国家口径：主体国家为美国；来源：美国专利商标局公开文件，商标98780858的Owner字段明确Scaled Cognition为Delaware, USA corporation。项目实际落地国家未单独披露，不以总部推断。

概述：专用代理模型发布和客户试点需要更低延迟与弹性容量。

流程：前线部署工程师（Forward Deployed Engineer）配置自定义模型服务，复用客户AWS环境并以Baseten Cloud提供溢出容量，调优路由与GPU分配，支撑模型发布和持续演示。

落地程度：模型发布完成并支持活跃POC；不将所有下游客户演示写成全面生产。

人工职责：客户研发团队迭代APT模型与评测；下游代理具体人工审批机制不在该案例中。

证据说明：客户故事Solutions明确Baseten 前线部署工程师（Forward Deployed Engineer）在Scaled Cognition模型发布和持续潜客演示的严格时间表内交付，列出自定义服务、AWS混合部署及弹性容量；是项目正文的岗位证据。

可切入环节：分析建议：选择一条低风险只读代理流程，分别测政策遵循、工具正确性和推理延迟。

- 整体延迟：降低40%。口径：Results自报，未披露完整负载和基线。

- 首token时间：低于120毫秒。口径：Results值，未标分位数，不视为完整代理任务耗时。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】自研APT代理模型需要在首发与正在进行的POC中同时证明质量、响应速度和可扩展性；还希望继续使用已有AWS投资，避免重复购买闲置容量。 [来源1](https://www.baseten.co/resources/customers/scaled-cognition-offers-ultra-fast-ai-agents-you-can-trust/)

### 工程师具体做了什么

- 【公开披露】FDE在紧迫发布周期内与客户联合基准测试既有负载，部署Custom Server、AWS与Baseten Cloud混合容量、区域化算力和请求路由。 [来源1](https://www.baseten.co/resources/customers/scaled-cognition-offers-ultra-fast-ai-agents-you-can-trust/)

### 技术方案与数据流程

- 【公开披露】项目以自有APT运行环境接入Custom Server，保留客户优化；AWS容量外接Baseten Cloud溢出容量，横向扩容支撑发布与研究实验。不是Baseten替客户训练APT或定义业务策略。 [来源1](https://www.baseten.co/resources/customers/scaled-cognition-offers-ultra-fast-ai-agents-you-can-trust/)

- 【公开披露】技术背景：自定义Docker服务器通过镜像、启动命令、服务端口、预测/readiness/liveness路径接入；标准模式由反向代理转发，定制HTTP日志需显式写request ID。文档也提供no-build路径，不能假定客户采用它。 [来源3](https://docs.baseten.co/development/model/custom-server)

- 【分析／复现建议】复现建议，非已公开实施：以同一任务集测端到端任务成功率、策略违例、工具调用与TTFT；给付款/账户变更等高影响动作设置人工审批，并验证跨云扩容失败回退。

### 解决程度与业务提升

- 【公开披露】案例报告整体延迟降低40%、TTFT低于120毫秒，并支持同时数百项研究实验。未披露每请求成本，且低TTFT不证明无幻觉或任务自动化率提高。 [来源1](https://www.baseten.co/resources/customers/scaled-cognition-offers-ultra-fast-ai-agents-you-can-trust/)

### 尚未公开的信息

- 【未披露】APT参数量、模型权重、服务镜像、GPU及区域名单、AWS/外部容量比例未公开。

- 【未披露】POC样本、基准对手、请求长度、并发和延迟分位未披露。

- 【未披露】客户实际人工审批、工具权限、策略评测指标与总成本未披露；Genesys覆盖客户数不是本项目部署数。

### 关键技能
- 分析：专用模型服务配置
- 分析：混合云突发容量
- 分析：代理负载与首token基准

### 风险
- 分析：模型行为与推理性能混淆
- 分析：混合云数据边界
- 分析：试点与正式客户范围混淆

### 限制
- Genesys覆盖8000多客户是下游平台规模，不视为本项目部署量。
- 本文不把供应商的确定性或无幻觉宣传当作独立验证事实。

### 来源
1. [Scaled Cognition offers ultra-fast AI agents you can trust](https://www.baseten.co/resources/customers/scaled-cognition-offers-ultra-fast-ai-agents-you-can-trust/)
2. [美国专利商标局公开文件](https://tmng-al.uspto.gov/resting2/api/casedoc/cms/case/99284016/office-action/OfficeAction7810198.pdf)
3. [Custom Docker containers](https://docs.baseten.co/development/model/custom-server)

## 57. Gamma：演示文稿图像生成的推理加速

国家：美国；项目落地：未披露
行业：演示文稿与视觉创作软件
国家口径：Gamma官方关于页说明团队位于美国旧金山；案例称支持全球用户，但没有逐国上线清单，因此不把总部等同部署国家。

概述：图像等待时间拖慢演示文稿生成，Gamma需要扩大吞吐而不自行组建模型基础设施团队。

流程：前线工程师与Gamma逐个评估图像模型质量和速度，优化运行时及副本规模，并把通过测试的模型接入真实图像生成流量。

落地程度：实际生产；供应商案例称每日生成超过300万张图片，并自2023年持续合作。

人工职责：Gamma团队设定并测试模型质量门槛，Baseten工程师持续优化；最终用户可编辑创作内容。生产内容逐图人工审核制度未披露。

证据说明：Baseten官方Gamma案例Solutions逐项目明确Forward Deployed Engineers（前线部署工程师）作为Gamma工程团队延伸，测试并优化图像模型；Results含客户联合创始人直接确认。

可切入环节：分析建议：从单一模板配图模型开始，固定质量评测集，比较延迟和每张图成本后灰度接入。

- 单模型图像生成速度：快30%–80%。口径：供应商按模型报告的范围，不等于所有模型统一快80%；原始样本与测试窗未公开。

- 副本资源效率：改善20%。口径：原文解释为减少副本数且未明显影响延迟，不是项目总成本减少20%。

- 整体成本与净节省：未公开。口径：虽称更具成本效率，未披露服务合同、推理单价和全成本净收益。

### 介入前的问题与基线

- 【公开披露】2023年起初以闭源生图为主；部分模型生成一张高分辨率图就约10秒，而Gamma希望整份演示在10秒内完成。团队无ML团队，希望降低延迟与规模成本。 [来源1](https://www.baseten.co/resources/customers/how-gamma-makes-building-presentations-criminally-fun/)

### 工程师具体做了什么

- 【公开披露】FDE对SDXL、Flux、Qwen等模型做质量和速度测试，新模型发布后数小时至数天优化，再提供API让Gamma用既有工作负载评估；Gamma保留产品与模型采用判断。 [来源1](https://www.baseten.co/resources/customers/how-gamma-makes-building-presentations-criminally-fun/)

### 技术方案与数据流程

- 【公开披露】已披露接入边界：模型经FDE部署为API端点→Gamma用已有工作负载测试→选中模型进一步优化并扩容。没有公开完整提示词、版式编排或图片入稿接口。 [来源1](https://www.baseten.co/resources/customers/how-gamma-makes-building-presentations-criminally-fun/)

- 【公开披露】技术背景：FLUX.1 dev示例把文本prompt提交预测端点，返回编码图片供应用解码。该公开模型卡列12B和H100 MIG 40GB，但不能当作Gamma实际配置；许可也需独立核查。 [来源3](https://www.baseten.co/library/flux-dev/)

- 【分析／复现建议】复现建议，非客户实现：固定提示词集、分辨率、种子和并发，人工盲评图像质量及品牌安全；比较等待时间和每张成本，并验证少副本情况下突发流量与失败重试。

### 解决程度与业务提升

- 【公开披露】案例正文给各模型生图快30%—80%、减少副本带来20%效率改善、每天超过300万图；未新增ML/基础设施岗位。7000万用户及1亿美元ARR是全公司背景，不能归因于本项目。 [来源1](https://www.baseten.co/resources/customers/how-gamma-makes-building-presentations-criminally-fun/)

### 尚未公开的信息

- 【未披露】各模型精确版本、推理步数、量化/编译方案、GPU、副本数、区域未公开。

- 【未披露】质量评估样本、盲评标准、内容审核与版权审核实现未披露。

- 【未披露】20%效率不是20%总成本降低；合同价、GPU账单、净节省和收入因果贡献未披露。

### 关键技能
- 分析：图像模型质量评测与基准测试
- 分析：推理运行时和副本容量优化
- 分析：新模型上线回归与降级

### 风险
- 分析：低延迟不能代替图像内容质量及版权审查
- 分析：用户总数并非受益于某项优化的因果样本

### 限制
- 是图像生成基础设施工程案例，不代表全部文稿业务效率同比提升。
- 70百万用户及收入是公司规模，不是工程模式独立造成的结果。

### 来源
1. [Baseten官方Gamma案例](https://www.baseten.co/resources/customers/how-gamma-makes-building-presentations-criminally-fun/)
2. [Gamma官方：团队所在地](https://gamma.app/about)
3. [FLUX.1 dev模型API示例](https://www.baseten.co/library/flux-dev/)

## 58. Latent Health：药事临床检索的多模型生产编排

国家：美国；项目落地：美国
行业：医疗药事与药品可及性软件
国家口径：Latent官方公司页列总部美国旧金山；Baseten本项目案例明确服务美国大型医疗系统，故落地业务列美国。数据中心地区未披露。

概述：临床文档需要识别、检索和问答，多模型挤在同一资源链路造成扩容瓶颈。

流程：将文字识别、嵌入检索、重排和问答模型拆成可独立扩容组件；分别分配计算资源，优化推理运行时及跨集群容错。

落地程度：真实生产；案例报告合作多年运行结果，并处理每日数百万文档量级的扩展需求。

人工职责：工程人员持续管理模型及系统；本基础设施案例未披露每项临床回答的人工复核制度，不将模型检索等同自动处方。

证据说明：Baseten官方案例Solutions明确Forward Deployed Engineers（前线部署工程师）与Latent工程团队优化多模型工作流，持续支持生产性能与可靠性。

可切入环节：分析建议：先优化只读药事文档检索并显示来源，保留专业人员的解释和决策责任。

- 服务可用性：99.999%。口径：供应商称合作期间达到的可用性；故障统计边界和原始日志未公开。

- 问答端到端延迟：P90为600毫秒。口径：P90（第90百分位）延迟，不是平均值或所有请求保证。

- 图形处理器利用率：改善6倍。口径：原文为GPU（Graphics Processing Unit，图形处理器）利用率；不可换算成全成本六分之一。

- 成本与净节省：未公开。口径：没有项目全成本和净现金节省披露。

### 介入前的问题与基线

- 【公开披露】既有大型云商直部署难以管理多模型及步骤；百万级每日文档量放大独立扩缩容缺失、单点故障和实验周期问题。输入覆盖病历笔记、化验、药物及媒体。 [来源1](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)

### 工程师具体做了什么

- 【公开披露】FDE与Latent工程师重构复合AI工作流，借Chains拆除处理瓶颈，并在运行时层比较/优化TensorRT-LLM与vLLM。 [来源1](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)

### 技术方案与数据流程

- 【公开披露】已披露流水线组件含OCR、微调问答LLM、自定义嵌入与重排。各步骤拆为可直接互调的Chainlet，OCR处理步骤置于CPU，AI模型运行GPU，各自选硬件并独立扩容。 [来源1](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)

- 【公开披露】运行可靠性依靠冷启动优化及跨集群扩容，迁移接口OpenAI兼容。公开说明并未给出医疗数据源连接器、向量库或完整检索提示模板。 [来源1](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)

- 【公开披露】技术背景：Chains使用Python定义组件和依赖，每个Chainlet声明硬件、软件和扩容参数，可本地mock测试。通用示例的Mistral/Phi模型不属于Latent已披露模型。 [来源4](https://www.baseten.co/products/chains/)

- 【分析／复现建议】复现建议，非已证实措施：把文档摄取/OCR吞吐与在线检索问答延迟分开验收；检查患者权限、引用对应、过期用药信息及专家复核，保留低置信度回退。

### 解决程度与业务提升

- 【公开披露】案例报告合作期间99.999%在线率、问答P90端到端600毫秒及GPU利用率提高6倍；这是推理系统指标，不能直接等同治疗提前、医务工作时长或费用降低。 [来源1](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)

### 尚未公开的信息

- 【未披露】模型与训练集、检索库、分块/重排规则、OCR错误处理、医疗质量指标未披露。

- 【未披露】GPU利用率绝对基线、在线率统计窗口/排除项、每阶段耗时与硬件数量未公开。

- 【未披露】实际患者数据隔离、审计日志保留、医疗专业人员复核和部署合同成本未披露。

### 关键技能
- 分析：多模型流水线拆分与背压
- 分析：弹性扩缩容、追踪与健康检查
- 分析：医疗文档访问控制与证据追踪

### 风险
- 分析：检索速度和可用性不是临床准确率
- 分析：医疗数据敏感，平台合规资质不自动证明客户端每个流程合规

### 限制
- 这是推理基础设施与检索编排案例，不是诊疗效果的独立研究。
- 吞吐与可用性均为供应商自报，无独立审计。

### 来源
1. [Baseten官方Latent案例](https://www.baseten.co/resources/customers/latent-delivers-pharmaceutical-search-with-baseten/)
2. [Latent官方公司页：总部](https://www.linkedin.com/company/latent-health)
3. [Latent官方信任中心：美国医疗系统](https://security.latenthealth.com/)
4. [Baseten Chains架构及示例](https://www.baseten.co/products/chains/)

## 59. Deliveroo：骑手入驻与餐厅状态语音运营

国家：英国；项目落地：未披露
行业：即时餐饮配送平台
国家口径：Deliveroo官方条款确认运营主体Roofoods Limited注册于英格兰与威尔士；案例仅称多地区多语言，未枚举落地国家。

概述：多地区骑手申请中断与餐厅状态核实依赖人工电话。

流程：语音联系闲置申请者、核实餐厅是否开门、催办Rider Check-In（骑手签到）标签；同一运营合作合并为一例。

落地程度：已上线；正文披露首几周与评估期实绩。

人工职责：本地运营人员处理特殊个案；实际接管比例未披露。

证据说明：案例作者署名 Forward Deployed Engineer；正文以共同开发口吻说明骑手签到标签激活代理，并引用客户对ElevenLabs工程团队部署支持的评价。

可切入环节：分析：从人工可复核的餐厅营业状态核实切入。

- 骑手后续行动：30%。口径：电话后7天内继续申请；不等于全部完成入职。

- 餐厅核实触达：75%。口径：评估期电话联系并核实营业状态的比例。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】骑手申请流程中途流失，人工重新联系耗时且地区间不一致；餐厅团队每周人工拨打数千电话核实骑手报告的关门状态。 [来源1](https://elevenlabs.io/blog/deliveroo)

### 工程师具体做了什么

- 【公开披露】FDE署名案例记载双方共同开发RCI标签激活代理；客户确认ElevenLabs工程团队支持高效部署。运营团队从重复联络转向特殊个案。 [来源1](https://elevenlabs.io/blog/deliveroo)

### 技术方案与数据流程

- 【公开披露】三个触发点分开：申请静止超过两周→按偏好语言确认继续意愿并指引；餐厅被标记可能关门→外呼核验营业时间并实时更新业务系统；标签送达五个工作日仍未激活→联系经理指导安装。 [来源1](https://elevenlabs.io/blog/deliveroo)

- 【分析／复现建议】复现建议，非客户已公开实现：建立三条独立漏斗：接通、确认、系统写入、实际完成；重试前查最新状态，避免重复催办或把语音信箱算完成。

- 【分析／复现建议】复现建议，非客户已公开实现：营业状态写回应保留通话证据、时间及人工纠错入口；对无人接听和回答含糊的情形保持未知，不能自动改成关门。

### 解决程度与业务提升

- 【公开披露】初期骑手触达超过80%，30%在来电后七天继续申请；餐厅核实成功75%，RCI站点触达86%。后两项不是订单增长或标签实际激活率；数千骑手联络从数天/周缩至数小时。 [来源1](https://elevenlabs.io/blog/deliveroo)

### 尚未公开的信息

- 【未披露】模型、电话供应商、系统API、身份验证、写入权限和转人工阈值未披露。

- 【未披露】各漏斗样本、对照组、激活净增量、误写率、部署周期与全口径成本未披露。

### 关键技能
- 分析：多语言语音编排
- 分析：运营系统状态写入

### 风险
- 分析：误判停业影响商家订单
- 分析：自动外呼应有明确身份与退出机制

### 限制
- 多个工作流属于同一合作，不拆成多个案例。
- 触达率、继续申请率与最终激活率是不同指标。

### 来源
1. [Deliveroo partners with ElevenLabs](https://elevenlabs.io/blog/deliveroo)
2. [Deliveroo Legal](https://deliveroo.co.uk/legal/)

## 60. Marshmallow：汽车保险自助保单服务

国家：英国；项目落地：英国
行业：汽车保险
国家口径：Marshmallow官方条款列伦敦注册办公地址；Sierra案例明确服务迁居英国客户的英国汽车保险业务。

概述：旧静态客服流程不能支持用户直接修改保单。

流程：接入客户API，处理地址/车辆变更、取消和续保，客服运营与QA共同设计旅程及合规边界。

落地程度：Marsha已处理真实客户会话。

人工职责：部分会话由人工参与；人工整体满意度仍更高。具体接管规则和比例未公开。

证据说明：官方逐项目记载Sierra负责大量实施、双方工程团队每日站会、每一两天更新，形成持续反馈部署循环；原文定位 daily standups。未公开正式前线部署工程师（Forward Deployed Engineer）职称，按嵌入式持续部署职责认定B。 属于同义职责证据，非原职位名。

可切入环节：分析：先做只读保单解释，再上线需明确确认的事务。

- AI会话满意度：超过82%。口径：客户自报CSAT；不是自动解决率，样本量和期间未知。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】旧支持由逐渐积累的固定流程构成，真正自助有限，客户无法直接修改保单；取消、续保及定价沟通涉及合规与情境判断。 [来源1](https://sierra.ai/customers/marshmallow)

### 工程师具体做了什么

- 【公开披露】Sierra承担大量实现；客户工程师和数据科学家共同塑造行为、学习Agent SDK并接入自有API。双方每日站会，每一两天发版；客服和运营映射旅程，QA参与准确性、语气与合规检查。这是嵌入式交付职责，未披露FDE职位名。 [来源1](https://sierra.ai/customers/marshmallow)

### 技术方案与数据流程

- 【公开披露】Marsha通过Agent SDK与客户API支持地址/车辆变更、取消、续保等旅程；人工保留适合人工介入的会话。IQS内部质量评分包含监管合规，是质量反馈依据。 [来源1](https://sierra.ai/customers/marshmallow)

- 【分析／复现建议】复现建议，非客户已公开实现：将对话理解与最终保费计算、政策资格及保单写入分开；客户确认变更前显示后果，失败时保留原保单和可追溯记录。

- 【分析／复现建议】复现建议，非客户已公开实现：固定测试集覆盖跨语言歧义、地址变更影响价格、取消退款及续保；同时监测IQS、CSAT、重复联系和升级率。

### 解决程度与业务提升

- 【公开披露】AI会话CSAT超过82%；内部IQS常高于平均人工，但整体人工CSAT仍更高。未给自动解决率或财务收益。 [来源1](https://sierra.ai/customers/marshmallow)

### 尚未公开的信息

- 【未披露】基础模型、API名称、检索方式、权限检查、定价决策边界、人工升级条件与逐次审批方式未披露。

- 【未披露】IQS权重、样本量、CSAT观察期、响应时延和成本未披露，不能推导AI优于全部人工。

### 关键技能
- 分析：保单事务API
- 分析：客服与合规联合评测

### 风险
- 分析：取消或改价误操作有财务后果
- 分析：不能从客服分数推出保险定价公平性

### 限制
- 正式前线部署工程师（Forward Deployed Engineer）职称未披露；证据为具体工程嵌入与连续部署实践。
- 20万是公司总客户数，不是AI使用量。

### 来源
1. [How Marshmallow uses AI](https://sierra.ai/customers/marshmallow)
2. [Marshmallow March competition terms](https://www.marshmallow.com/march-competition-terms)

## 61. Sutherland Excavating Ltd.：石油储罐检查与异常监测

国家：加拿大；项目落地：加拿大
行业：石油储罐维护与现场工程服务
国家口径：客户官方联系页列加拿大New Brunswick公司地址；Hashlogics具名客户案例明确Region:Canada并说明真实站点运行，故公司及部署均列加拿大。

概述：纸质巡检及分散缺陷记录难以跟踪现场问题。

流程：物联网数据进入AWS管道，异常提醒、巡检安排、缺陷工单和承包商协作共用多租户权限体系。

落地程度：已上线独立客户子域，后续随新站点持续调优。

人工职责：现场经理、承包商等五层角色参与处置；是否每条预测经人工批准未知。

证据说明：官方前线部署工程师（Forward Deployed Engineer）页逐项目点名Sutherland，说明工程师在客户系统内构建并参加次日站会处理反馈；案例Run段确认持续调优。

可切入环节：分析：先做只读异常提示并由现场人员复核。

- 人工错误：减少40%。口径：客户自报；定义、样本和对照期未披露。

- 维护周转：加快20%。口径：供应商报告；计算口径未披露。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】原先用纸质记录和表格跟踪检查，易漏检；缺少实时站点信息，维修偏被动，承包商缺陷协作分散，难扩展到多站点。 [来源1](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)

### 工程师具体做了什么

- 【公开披露】工程师梳理检查→缺陷→供应商工单，设计租户隔离与共享IoT管道，并在上线后持续调优维护模型和仪表盘。 [来源1](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)

- 【公开披露】FDE服务页逐项目说明Sutherland系统按客户真实流程构建，工程师次日参加站会处理反馈；通用合同条款不等于本项目合同。 [来源2](https://www.hashlogics.com/hire/forward-deployed-engineers)

### 技术方案与数据流程

- 【公开披露】AWS承载传感器管道、告警模型、检查引擎和支付门户；油罐液位数据支持异常提醒，缺陷进入升级/工单流程。独立子域分租户，五级角色控制；Vue.js、Laravel、React Native为披露技术栈，PayPal用于承包商付款。 [来源1](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)

- 【公开披露】AWS RDS静态加密、TLS 1.3传输、JWT/bcrypt、审计日志、限流及CSRF保护；站点文档有版本控制。没有公开LLM，不能把预测维护自动称为生成式智能体。 [来源1](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)

- 【分析／复现建议】复现建议，非客户已公开实现：现场异常需按漏报和误报分别验收；传感器断流、校准偏差和跨租户访问应进入测试，付款和高风险维护保留人工批准。

### 解决程度与业务提升

- 【公开披露】客户报告人工错误少40%、运营开销少30%、检查准确度高30%、维护周转快20%；计算定义和对照期未公开，运营开销并不等同已审计净现金节省。 [来源1](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)

### 尚未公开的信息

- 【未披露】告警算法、训练数据、阈值、模型版本、预测提前量与验证集未披露。

- 【未披露】传感器数量、实际活跃站点、付款批准流程、工单关闭验收、实施报价及净收益未披露。

### 关键技能
- 分析：IoT异常与数据缺口
- 分析：多租户隔离与工单闭环

### 风险
- 分析：传感器故障误报或漏报
- 分析：安全关键巡检不可仅靠模型

### 限制
- 供应商发布的客户口径，未独立审计。
- 不是大语言模型客服，属于前线部署工程师（Forward Deployed Engineer）物联网与机器学习生产部署。

### 来源
1. [TankAware AI + IoT Petroleum Site Management](https://www.hashlogics.com/case-studies/tankaware-ai-iot-petroleum-site-management)
2. [Hire forward deployed engineers who ship inside your operations](https://www.hashlogics.com/hire/forward-deployed-engineers)
3. [Sutherland Excavating Contact](https://www.sutherlandexcavating.com/contact-us/)

## 62. ZhoopZhoop：汽修连锁语音接待与配件询价

国家：加拿大；项目落地：加拿大
行业：多门店汽车维修服务
国家口径：客户官方门店页列加拿大安大略主要经营地址；供应商部署案例明确Toronto, Canada并说明已推广多点，故公司与部署均列加拿大。

概述：维修人员忙于修车，漏接预约并需逐家致电配件商。

流程：Twilio/Deepgram语音接待写入预约日历；外呼供应商收集报价，汇总到多门店仪表盘；WhatsApp提供同类预约入口。

落地程度：多维修门店已经上线，使用Sentry监控真实工作流。

人工职责：门店经理、前台、采购团队查看记录及报价；自动采购授权和逐次人审规则未公开。

证据说明：官方前线部署工程师（Forward Deployed Engineer）页逐项目明确该系统在客户自有流程和系统内构建，工程师参与站会反馈；案例Run段记载用真实通话记录调优并监控。

可切入环节：分析：先做预约查询和询价比较，采购保留人工决策。

- 量化成效：未披露。口径：未公布接通量、预约转化或节省工时。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】技师接电话会打断维修，造成漏接和漏预约；逐家供应商询价依赖人工，报价分散，多门店电话及WhatsApp处理不一致。 [来源1](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)

### 工程师具体做了什么

- 【公开披露】团队先画出入呼预约和外呼询价两条流程，再交付FastAPI后台与React仪表盘，多门店上线后用真实转录调优并以Sentry监控。 [来源1](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)

- 【公开披露】官方FDE页具名说明工程师在客户系统内按门店流程构建，并参加站会接收生产问题。 [来源2](https://www.hashlogics.com/hire/forward-deployed-engineers)

### 技术方案与数据流程

- 【公开披露】已公开数据流：Twilio接入电话→Deepgram转写/轮次处理→OpenAI Chat Completions推理与函数调用→FastAPI查日历写预约→Deepgram语音确认→WebSocket向仪表盘推送预约及转录。外呼按请求收集供应商库存和价格，返回比较，不等于自动采购。 [来源1](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)

- 【公开披露】后台存通话记录、转录及AI摘要；PostgreSQL、Celery/Redis、AWS S3、FullCalendar、PyMuPDF报价文档解析列于栈中。JWT配HTTP-only刷新cookie、角色权限、受保护webhook、HTTPS和bcrypt；经理、前台、采购各有角色。 [来源1](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)

- 【分析／复现建议】复现建议，非客户已公开实现：验收以预约真实落库且无重复为准；模拟并发抢占、时区/改约、口音、噪声和供应商听错价格，设置人工修正及重试幂等。

### 解决程度与业务提升

- 【公开披露】已在多维修点上线，员工可统一查看通话、录音、转录、报价和预约；无公开接通率、预约转化、节省工时或财务结果。 [来源1](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)

### 尚未公开的信息

- 【未披露】OpenAI具体模型、提示词、工具参数、录音保留期、授权同意、转人工策略及正式评测集未披露。

- 【未披露】部署时间、门店数量、通话量、延迟分位数、重复预约率、实施费与每通成本未披露。

### 关键技能
- 分析：语音与工具调用
- 分析：日历并发控制和报价结构化

### 风险
- 分析：重复预约或错误零件型号
- 分析：通话记录与供应商报价保密

### 限制
- 没有证据证明系统自主下采购订单；已确认的是外呼收集报价。

### 来源
1. [ZhoopZhoop AI Receptionist for Auto Shops](https://www.hashlogics.com/case-studies/zhoopzhoop-ai-collision-shop-platform)
2. [Hire forward deployed engineers who ship inside your operations](https://www.hashlogics.com/hire/forward-deployed-engineers)
3. [ZhoopZhoop service locations](https://zhoopzhoopauto.com/locations/)

## 63. Bilt：住房支付与奖励客服

国家：美国；项目落地：未披露
行业：住房支付与会员奖励平台
国家口径：Bilt官方公告确认公司总部在纽约；该AI客服实际覆盖国家未单独披露。

概述：复杂金融服务咨询需要遵循安全与合规协议。

流程：AI代理处理金融服务查询；具体API和可执行资金操作未公开。

落地程度：已部署并披露解决率。

人工职责：人工审核、升级规则和接管比例未披露。

证据说明：Decagon工程师官方文章在Agent Engineer现场案例中明确团队为Bilt构建金融查询代理；同文定义该角色直接嵌入客户并持续迭代生产。 Agent Engineer（人工智能代理工程师）为同义职责证据，非原前线部署工程师职位名。

可切入环节：分析：从有出处的奖励与支付说明切入。

- 查询解决率：70%。口径：供应商工程文章自报；分母、样本期和成功判定未披露。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【未披露】官方角色文章只概述复杂金融服务咨询，未披露原客服系统、人工处理时长或旧解决率。

### 工程师具体做了什么

- 【公开披露】Decagon创始工程师Amy Jin在Agent Engineer文章中具名确认团队为Bilt构建金融咨询代理。该角色负责嵌入客户、设计、部署和生产迭代；不是已核验的FDE正式职称。 [来源1](https://decagon.ai/blog/introducing-agent-engineer)

### 技术方案与数据流程

- 【公开披露】本项目可确认的是金融咨询支持及合规、安全要求；未公布实际数据流、API、知识库、模型或可写操作。角色文章一般性的提示链、路由、回退能力不能逐项套入Bilt。 [来源1](https://decagon.ai/blog/introducing-agent-engineer)

- 【分析／复现建议】复现建议，非客户已公开实现：先把只读账户解释与真实资金/信用决策划开；用已脱敏历史咨询验证答案、权限过滤和人工转接，任何扩权需单独验收。

- 【分析／复现建议】复现建议，非客户已公开实现：定义解决为问题正确闭环且观察期内未重开，分别记录人工接管和用户放弃，避免将退出对话算解决。

### 解决程度与业务提升

- 【公开披露】角色文章报告70%解决率，但分母、问题范围、时间窗和成功标准均未给出。链接所指Bilt独立案例本次重定向到案例目录，不能补出更多项目技术细节。 [来源1](https://decagon.ai/blog/introducing-agent-engineer)

### 尚未公开的信息

- 【未披露】客户侧负责人、基线、渠道、部署范围、评测集、上线迭代周期、人工控制和底层模型未披露。

- 【未披露】70%是否含人工帮助、合规失败率、客户满意度、合同价及净节省未披露。

### 关键技能
- 分析：金融问答溯源
- 分析：敏感操作权限隔离

### 风险
- 分析：错误账务解释
- 分析：不得把解决率当金融操作准确率

### 限制
- 原详细客户页目前转向客户索引；采用仍公开的工程师官方文章，技术细节有限。

### 来源
1. [Introducing the Agent Engineer: Where AI meets real-world impact](https://decagon.ai/blog/introducing-agent-engineer)
2. [Bilt announces New York headquarters](https://newsroom.biltrewards.com/bilt-announces-new-headquarters-in-new-york-citys-meatpacking-district)

## 64. Rippling：多产品客服分流与账户查询

国家：美国；项目落地：未披露
行业：人力资源、薪酬与IT管理软件
国家口径：公司官方隐私通知列美国加州地址，country按主体国家填美国；该客服部署覆盖国家未披露。

概述：旧客服树难以处理跨产品问题和复杂路由。

流程：接入内部Application Programming Interface（应用程序编程接口）查询账户信息；按产品标签路由，必要时转专家，聊天及邮件共用支持能力。

落地程度：已上线；供应商称支持12+产品线、40万用户。覆盖人数不等于实际AI使用人数。

人工职责：专家处理升级工单；Agent Assist辅助客服。逐条审批要求与实际人工升级率未披露。

证据说明：Decagon官方客户案例Solution第4项直接标明Forward-Deployed Engineering Support（前线部署工程支持），并描述工程师为Rippling定制系统接口、一天内替换停用工具及持续现场支持。

可切入环节：分析：从只读账户查询与人工转接摘要切入。

- 聊天分流率：38%升至50%以上。口径：供应商自报；并非准确率。页面32%增幅为相对提升，不是增加32个百分点。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】旧决策树难处理模糊问题与不同客户流程，常误路由；聊天自助约38%，邮件没有AI。HR、薪酬及IT等12余产品需要不同专家。 [来源1](https://decagon.ai/case-studies/rippling)

### 工程师具体做了什么

- 【公开披露】明确FDE工程支持：双方定制API和路由，识别75余标签及升级场景；一次旧产品紧急停用时，一天内以Agent Assist替换并适配品牌语气。 [来源1](https://decagon.ai/case-studies/rippling)

### 技术方案与数据流程

- 【公开披露】已有知识库及历史工单加内部API提供上下文，例如查员工医疗保险登记状态；代理追问澄清，再回答或执行动作。75余标签将会话送到合适专家，人工客服另用AI Assist维持回复质量。 [来源1](https://decagon.ai/case-studies/rippling)

- 【分析／复现建议】复现建议，非客户已公开实现：按管理员/员工和产品权限建立接口授权矩阵；回答可见范围必须由后端校验，不能仅由对话模型判断。

- 【分析／复现建议】复现建议，非客户已公开实现：分别评估模糊问题澄清、跨产品标签、多意图路由、无权限查询及升级；API停用应有兼容测试与回退。

### 解决程度与业务提升

- 【公开披露】聊天分流从38%升至50%以上，页首32%是相对增幅口径；另报告路由即时改善7%，未说明百分点或相对值。上线AI邮件分流，覆盖40万用户是服务范围，非40万已实际使用AI。 [来源1](https://decagon.ai/case-studies/rippling)

### 尚未公开的信息

- 【未披露】模型、API清单、写入操作范围、身份校验、知识更新机制、完整路由规则与评测样本未披露。

- 【未披露】邮件分流率、7%路由改善定义、CSAT对照、工程费用和全口径节省未披露。

### 关键技能
- 分析：API权限隔离
- 分析：多产品路由评测

### 风险
- 分析：员工福利和薪酬信息可能越权泄露
- 分析：错误路由拖延敏感问题

### 限制
- 指标未经独立审计；不将自助分流解释为业务问题已正确解决。

### 来源
1. [How Rippling supports many user types with Decagon](https://decagon.ai/case-studies/rippling)
2. [Rippling User Privacy Notice](https://static-assets.ripplingcdn.com/legal/en-US/user_privacy_notice.html)

## 65. Curology：皮肤护理订阅与物流客服

国家：美国；项目落地：美国
行业：远程皮肤护理与处方护肤品
国家口径：Curology官方联系页列圣迭戈办公室；案例明确服务美国患者，故公司及客服业务国家均列美国。

概述：人工客服横跨邮件、短信与聊天，重复处理订阅物流问题。

流程：统一聊天、短信及邮件，处理地址、补发、暂停发货、退款请求和物流查询；Agency同属此项目，不另计。

落地程度：已用于真实客服。

人工职责：医疗问题限于适合AI的范围，并设置升级规则；皮肤科专业人员仍提供处方。实际人工接管比例未公开。

证据说明：Agent Engineer（智能体工程师）同义职责证据，非原职位名Forward Deployed Engineer（前线部署工程师）。Decagon工程负责人在同一官方文章明确该角色直接嵌入客户、负责生产迭代，并逐项目点名Curology由该角色完成工作；客户案例独立确认真实使用。

可切入环节：分析：先做物流查询并将医学问题转专业人员。

- 客服运营成本：下降65%。口径：供应商自报；绝对费用、期间及是否包含全部实施成本未知。

- 聊天渠道占比：5%升至80%。口径：这是客服流量渠道占比，不是80%自动解决率。

### 介入前的问题与基线

- 【公开披露】原邮件、短信、表单和聊天均须人工逐条处理，即使使用模板也需人工；聊天仅占5%，实时排班难平衡，增长又不希望同步增加人数。 [来源1](https://decagon.ai/case-studies/curology)

### 工程师具体做了什么

- 【公开披露】Agent Engineer文章明确一名工程师将数十个重复流程改造成自主订阅管理与物流查询；属于嵌入式Agent Engineer职责证据。 [来源2](https://decagon.ai/blog/introducing-agent-engineer)

- 【公开披露】项目将支持统一到代理系统，并为同集团Agency设独立帮助中心、升级协议和业务规则，保留品牌差异。 [来源1](https://decagon.ai/case-studies/curology)

### 技术方案与数据流程

- 【公开披露】客户可更新地址、补发订单、取消/暂停/延迟发货、申请退款及查物流，覆盖聊天、短信与邮件。客户要求医疗相关问题只由AI处理适当范围，但具体医疗升级规则未公开。 [来源1](https://decagon.ai/case-studies/curology)

- 【分析／复现建议】复现建议，非客户已公开实现：订阅和物流操作应与临床建议分开；退款请求不等于退款自动批准，需在服务端限制金额、权限及重试重复操作。

- 【分析／复现建议】复现建议，非客户已公开实现：按两个品牌分别测政策、帮助中心检索及升级，验证跨渠道身份关联不会泄露健康信息。

### 解决程度与业务提升

- 【公开披露】客服运营成本报告下降65%，未披露绝对成本及是否覆盖实施维护；聊天承担流量从5%升至80%，属于渠道迁移，不能写成80%问题由AI独立解决。 [来源1](https://decagon.ai/case-studies/curology)

### 尚未公开的信息

- 【未披露】模型、后台API、临床问题拒答/升级规则、患者认证及健康信息存储保留未披露。

- 【未披露】成本基线期、净节省、处方相关操作权限、自动解决率和质量样本未披露。

### 关键技能
- 分析：订阅事务编排
- 分析：医疗与商业问题分流

### 风险
- 分析：不能把账单客服当诊疗系统
- 分析：退款与发货变更须保留审计

### 限制
- 未证明改善任何医学结局；65%是客服运营成本口径，总投入未知。
- B级基于官方同义岗位职责与具名项目的组合；不能说原文把该项目工程师职位写成Forward Deployed Engineer（前线部署工程师）。

### 来源
1. [Customer Success Story: Curology + Decagon](https://decagon.ai/case-studies/curology)
2. [Introducing the Agent Engineer: Where AI meets real-world impact](https://decagon.ai/blog/introducing-agent-engineer)
3. [Contact Curology](https://curology.com/contact-us/)

## 66. Noom：健康管理订阅客服现代化

国家：美国；项目落地：未披露
行业：数字健康与体重管理服务
国家口径：Noom官方公告列总部Princeton, NJ，country为美国；项目国家未具体披露。

概述：年初客服高峰使旧规则式平台难以扩展。

流程：迁出第一代工作流驱动平台，用AI客服处理聊天与常规支持请求。

落地程度：已上线，披露上线30天后的分流变化。

人工职责：人工转接条件、医学问题边界和实际人审比例未披露。

证据说明：Agent Engineer（智能体工程师）同义职责证据，非原职位名Forward Deployed Engineer（前线部署工程师）。Decagon工程负责人在同一官方文章明确该角色直接嵌入客户、负责生产迭代，并逐项目点名Noom由该角色完成工作；客户案例独立确认真实使用。

可切入环节：分析：从非临床订阅与账户问答切入。

- 客服分流率：59%升至68%。口径：30天内增加9个百分点；不是减少68%全部人员。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】迁移前是第一代工作流驱动客服平台；年初咨询量显著上涨，旧分流率59%，需要更灵活的支持。 [来源1](https://decagon.ai/case-studies/noom)

### 工程师具体做了什么

- 【公开披露】官方角色文章逐项点名一名Agent Engineer改造Noom支持基础设施；直接客户页确认迁移及上线效果。正式FDE职称未披露。 [来源1](https://decagon.ai/case-studies/noom) [来源2](https://decagon.ai/blog/introducing-agent-engineer)

### 技术方案与数据流程

- 【公开披露】客户页列使用Chat，确认从旧工作流平台迁往AI支持；未说明订阅、医疗、教练等具体用例及后台动作。通用Decagon功能不能填补该项目架构。 [来源1](https://decagon.ai/case-studies/noom)

- 【分析／复现建议】复现建议，非客户已公开实现：迁移时先从旧流程提取意图、升级点与政策，影子比较新旧回复；年初旺季应单独切片，避免把季节流量差异当模型提升。

- 【分析／复现建议】复现建议，非客户已公开实现：区分常规账户支持和健康建议，核验何时必须升级；同时记录重复来访、投诉与错误分流，防止只优化分流率。

### 解决程度与业务提升

- 【公开披露】30天内分流从59%升到68%，增加9个百分点；不是减少68%全部客服人员。案例宣称维持质量，但没有公开独立质量评分。 [来源1](https://decagon.ai/case-studies/noom)

### 尚未公开的信息

- 【未披露】模型、知识来源、工具/API、人工批准、健康问题边界、渠道间记忆和部署区域未披露。

- 【未披露】咨询量、分流计算公式、复联率、抽样方法、CSAT数字和成本未披露。

### 关键技能
- 分析：旧客服迁移
- 分析：健康问题边界评测

### 风险
- 分析：健康敏感数据保护
- 分析：分流率不能替代安全性或解决率

### 限制
- 病例结局与客服准确率未披露；不能推断健康管理已自动化。
- B级基于官方同义岗位职责与具名项目的组合；不能说原文把该项目工程师职位写成Forward Deployed Engineer（前线部署工程师）。

### 来源
1. [How Noom is scaling concierge experiences](https://decagon.ai/case-studies/noom)
2. [Introducing the Agent Engineer: Where AI meets real-world impact](https://decagon.ai/blog/introducing-agent-engineer)
3. [Noom Appoints Jim Bugden Chief Financial Officer](https://www.noom.com/in-the-news/noom-appoints-jim-bugden-chief-financial-officer/)

## 67. Klarna：美国第一线语音客服

国家：英国；项目落地：美国
行业：消费支付与分期付款服务
国家口径：官方治理页确认Klarna Group plc在英国注册、Klarna Bank AB在瑞典注册；country采用集团主体英国。项目官方案例明确落地美国。

概述：简单支付状态与产品问题也需排队等待人工。

流程：第一线语音回答信息型问题、收集背景，复杂或敏感情形以及用户要求时转人工。

落地程度：美国已上线；面向3500万美国客户可用，全球扩展仍是计划。

人工职责：用户需要时可接通人工；实际转人工比例未披露。

证据说明：ElevenLabs前线部署工程师服务页刊载Klarna产品经理对Forward Deployed Engineer（前线部署工程师）团队共同构建、迭代的直接评价，排除只有客户标志的泛关联；另一官方案例确认美国电话客服已上线。评价未逐字指定美国电话功能，按双源组合B级记录。

可切入环节：分析：先做支付状态说明与人工转接。

- 解决速度：最高10倍。口径：限由代理处理的问题；没有全体来电对照、样本或绝对基线。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】信息型来电如产品指导、付款状态和后续步骤原本也须排队等人工，拉长等待并占用客服。 [来源1](https://elevenlabs.io/blog/klarna)

### 工程师具体做了什么

- 【公开披露】美国电话第一线已上线；FDE服务页有Klarna产品经理对共同构建、迭代的具名公司评价，但评价未逐字限定美国电话功能，因此为双源组合证据。 [来源1](https://elevenlabs.io/blog/klarna) [来源2](https://elevenlabs.io/agents/forward-deployed-engineers)

### 技术方案与数据流程

- 【公开披露】ElevenAgents处理信息查询、收集上下文，复杂/敏感问题或用户想要人工时转接。选型看低延迟、数据驻留选项、编排与分析，以及更换语言模型的灵活性；这些选型理由不证明启用了每个具体安全配置。 [来源1](https://elevenlabs.io/blog/klarna)

- 【分析／复现建议】复现建议，非客户已公开实现：把身份验证、付款状态查询和执行付款分开定义工具；验收必须覆盖用户主动要求人工、敏感投诉和转接队列不可用。

### 解决程度与业务提升

- 【公开披露】对代理处理的问题，解决最高快10倍；开放给3500万美国客户是可用范围，不是实际通话数。覆盖全球1.14亿客户是后续计划，不能计作已部署。 [来源1](https://elevenlabs.io/blog/klarna)

### 尚未公开的信息

- 【未披露】具体模型、电话/CRM接口、身份验证、知识源、数据驻留地点及评测流程未披露。

- 【未披露】10倍基线、通话样本、自动解决占比、复杂度校正、完整成本和净收益未披露。

### 关键技能
- 分析：语音低延迟编排
- 分析：金融客服升级路径

### 风险
- 分析：身份认证与付款信息保护
- 分析：不得把可用人数等同实际使用

### 限制
- 以Klarna Group plc法律主体国家标注英国；银行子公司瑞典。不要混为同一总部概念。
- 不把11400万全球扩展计划写为已部署。
- 客户的前线部署团队参与有明确评价，但评价页没有将美国电话流程逐项绑定；不把组合关联升级为单页项目级证据。

### 来源
1. [Klarna reduces Time to Resolution by 10X with ElevenAgents](https://elevenlabs.io/blog/klarna)
2. [ElevenLabs Forward Deployed Engineers](https://elevenlabs.io/agents/forward-deployed-engineers)
3. [Klarna Governance Oversight](https://investors.klarna.com/governance/Governance-Oversight/)

## 68. T-Mobile：App内文本与语音客户支持

国家：美国；项目落地：未披露
行业：电信运营
国家口径：本例客户是T-Mobile US，美国主体，官方投资者问答列总部为华盛顿州贝尔维尤。该语音功能的一手访谈未逐项公布上线国家与地区，暂不把美国总部直接当作部署范围。

概述：账单、订阅和网络服务问题需要接入CRM与旧业务系统；仅模型回答不能完成服务。

流程：将模型编排接入企业工具和API网关，结合语音延迟、打断与测试优化。不能把IntentCX公告全部规划视为同一已投产功能。

落地程度：2025-09-11 OpenAI 平台负责人一手访谈称 T-Mobile app 部分语音功能已由 OpenAI 模型处理；不要据此认定全量客服均已被替代。

人工职责：客户服务人员借助个性化建议处理客户问题；部分交互自动化；需要时执行任务须获客户许可。具体人工升级率和裁撤岗位比例未公开。

证据说明：OpenAI负责人在BG2访谈明确称 FDE（Forward Deployed Engineer，前线部署工程师）嵌入T-Mobile进行集成；官方另确认T-Mobile试点Frontier方法。访谈内容通过可读转写核验，本次未独立复听原视频。

可切入环节：先切入账单解释、故障排查和转人工摘要，避免第一阶段直接修改账户。

- 效率与解决程度：无可归因的已实现量化披露。口径：一手访谈称部分App功能已用OpenAI模型；未找到该项目独立的解决率、节时或吞吐指标。

- 成本变化：未公开。口径：访谈称合作约一年；未找到能单独归因于该 FDE（Forward Deployed Engineer，前线部署工程师） 项目的已实现节时、成本或解决率数字；合同额、部署费用未公开。

### 介入前的问题与基线

- 【公开披露】2024年IntentCX公告描述传统规则式下一步建议受有限数据和固定动作库制约；这是合作背景与计划，不能当作已上线语音系统的量化基线。 [来源2](https://www.t-mobile.com/news/business/t-mobile-launches-intentcx-with-openai)

### 工程师具体做了什么

- 【公开披露】BG2参与者访谈可读转写描述FDE深嵌T-Mobile，搭建系统集成及音频评测；本次读取转写全文，未独立复听原视频。OpenAI另确认其试点Frontier方法。 [来源4](https://bidclub.ai/e/inside-openai-enterprise-forward-deployed-engine) [来源3](https://openai.com/index/introducing-openai-frontier/)

### 技术方案与数据流程

- 【公开披露】访谈T-Mobile段落确认App中已有部分文本/语音支持由OpenAI模型承接；工程工作包括模型编排、接CRM等工具、为无清晰接口的系统搭API网关，以及定义黄金评测。五分钟音频会话是否正确闭环难评分，需优化延迟与打断。 [来源4](https://bidclub.ai/e/inside-openai-enterprise-forward-deployed-engine)

- 【公开披露】参与者称该客户反馈进入Realtime GA模型快照改进；并未披露客户模型版本、评分集或达到的绝对成功率。IntentCX公告中客户数据、网络数据与交易系统整合属于规划范围。 [来源4](https://bidclub.ai/e/inside-openai-enterprise-forward-deployed-engine) [来源2](https://www.t-mobile.com/news/business/t-mobile-launches-intentcx-with-openai)

- 【分析／复现建议】复现建议，非客户已公开实现：按查询、诊断、变更套餐等权限拆分工具，评估全通话而非单轮文本；测插话恢复、长时间静音、噪声和人工转接，保留旧渠道降级。

### 解决程度与业务提升

- 【未披露】未找到可单独归因该FDE语音项目的已实现时间、解决率或成本数字；不能挪用Frontier文中匿名其他行业收益。

### 尚未公开的信息

- 【未披露】生产覆盖比例、全部上线功能、模型快照、后端网关清单、身份认证和审批门槛未公开。

- 【未披露】语音黄金集、人工评分标准、延迟分位数、回退流程、项目投入与净收益未公开。

### 关键技能
- 旧系统API封装
- 工具权限与事务一致性
- 音频端到端评测
- 用户授权、失败回滚与升级

### 风险
- 客户许可不能由模型自行假定
- 改套餐或账单等动作需要明确授权与可回滚记录

### 限制
- 2024 资本市场日的减少 75% inbound contacts 是多项数字化及 AI 工作共同的未来目标，不是 IntentCX/FDE（Forward Deployed Engineer，前线部署工程师） 已实现结果。
- B级为一手发言的组合证据；不与逐项目官方书面记录等同。

### 来源
1. [Inside OpenAI Enterprise: Forward Deployed Engineering, GPT-5, and More | BG2 Guest Interview](https://www.youtube.com/watch?v=yLTSqBzKG2s)
2. [T-Mobile and OpenAI Join Forces](https://www.t-mobile.com/news/business/t-mobile-launches-intentcx-with-openai)
3. [OpenAI官方：Frontier与T-Mobile试点](https://openai.com/index/introducing-openai-frontier/)
4. [原始访谈可读转写（非官方逐字稿）](https://bidclub.ai/e/inside-openai-enterprise-forward-deployed-engine)
5. [T-Mobile US官方：总部问答](https://investor.t-mobile.com/resources/investor-faqs/default.aspx?INTNAV=tNav%3AInvestors%3AResources)

## 69. Revolut：多语种第一线语音客服

国家：英国；项目落地：英国、欧洲（未逐国披露）
行业：数字金融与银行服务
国家口径：Revolut官方说明全球总部位于英国伦敦。ElevenLabs本项目官方案例明确上线范围为英国及欧洲，但没有公布全部欧洲国家清单；不把31种语言等同31个国家。

概述：自研语音原型可行，但实时轮流说话、测试监控、支付数据保护和多语扩容成为生产瓶颈。

流程：案例直接确认 FDE（Forward Deployed Engineer，前线部署工程师）参与。语音代理接入Revolut自有系统，回答账户相关问题并在适用时处理争议/拒付；Revolut保留编排和业务逻辑。

落地程度：英国及欧洲已规模上线，覆盖400万+客户，31种以上语言。覆盖人数不是实际使用人数。

人工职责：人类团队保留业务逻辑和治理控制；项目未公开人工转接率、全自动解决率或争议决策复核比例。

证据说明：案例直接确认 FDE（Forward Deployed Engineer，前线部署工程师）参与。语音代理接入Revolut自有系统，回答账户相关问题并在适用时处理争议/拒付；Revolut保留编排和业务逻辑。

可切入环节：先做已认证用户的只读状态查询和人工转接摘要；金额相关执行单独设权限与复核。

- 效率与使用规模：供应商称工单少于5分钟解决，过去平均用时至少其8倍；比较含排队且未按问题复杂度校正。99.7%是通话成功进行率，不是财务问题解决准确率。。口径：客户或供应商自报；详见口径限制

- 成本变化：未披露每分钟、每工单总成本或项目净节省，仅称价格具有竞争力。。口径：未披露项目总投入和净节省

### 介入前的问题与基线

- 【公开披露】内部语音原型证明可行，但把STT、LLM和TTS投入生产，还需轮次处理、测试监控及PCI/零保留控制，形成平台级负担；目标是规模化语音支持而保留成本和业务控制。 [来源1](https://elevenlabs.io/blog/revolut)

### 工程师具体做了什么

- 【公开披露】客户明确肯定FDE响应速度；多供应商对比后选择ElevenLabs，Revolut继续拥有编排与业务逻辑，保留内部模型及既有聊天/数字AI系统。 [来源1](https://elevenlabs.io/blog/revolut)

### 技术方案与数据流程

- 【公开披露】来电实时识别切换语言，经安全API连接自有系统，以实时账户上下文答疑，并在适用时处理争议与拒付。供应商提供语音质量、轮次处理和可靠性；页面提PCI合规及零保留选项，未公开逐项部署配置。 [来源1](https://elevenlabs.io/blog/revolut)

- 【公开披露】工程方法文章介绍按成功标准建立测试、从生产转录生成回归用例、版本化及分支小流量验证。这是供应商方法背景，不证明Revolut逐项采用。 [来源2](https://elevenlabs.io/blog/building-voice-agents-that-last-some-lessons-learned-from-forward-deployed-engineering)

- 【分析／复现建议】复现建议，非客户已公开实现：将接通成功、业务正确解决、资金动作授权分别监测；争议和拒付需服务端校验身份、状态与权限，避免重试产生重复操作。

### 解决程度与业务提升

- 【公开披露】英国及欧洲覆盖400多万客户，31余语言；工单少于5分钟，对比旧处理至少8倍时长，但包含排队且未控制复杂度。99.7%是通话成功进行率，非金融正确率。 [来源1](https://elevenlabs.io/blog/revolut)

### 尚未公开的信息

- 【未披露】客户模型版本、API、权限边界、人工审批/升级、选型测试集及回归阈值未披露。

- 【未披露】零保留具体启用范围、独立审计、对照窗口、每分钟或每工单费用及净收益未披露。

### 关键技能
- 语音/电话集成、身份验证、最小权限工具调用、多语言回归测试、轨迹观测、零保留配置与数据边界。

### 风险
- 账户信息泄露、误操作和错误拒付处理；平台认证不自动等于整个部署合规。

### 限制
- 非随机对照；样本量和测量窗口未公开。不可把8倍用时差直接写成87.5%成本下降。

### 来源
1. [ElevenLabs官方客户案例：工程师参与与完整指标口径](https://elevenlabs.io/blog/revolut)
2. [ElevenLabs工程师：生产部署与持续评测方法](https://elevenlabs.io/blog/building-voice-agents-that-last-some-lessons-learned-from-forward-deployed-engineering)
3. [Revolut官方：伦敦全球总部](https://www.revolut.com/blog/post/where-is-revolut-based/)

## 70. Hydro-Québec 的 Electric Circuit（Circuit électrique）：Voltère 网站咨询助手

国家：加拿大；项目落地：加拿大
行业：公共电动车充电
国家口径：运营主体Hydro-Québec总部在加拿大蒙特利尔；供应商本项目案例明确服务魁北克公共充电网络。网站可从境外访问不等于项目在其他国家落地。

概述：充电服务增长带来重复咨询，团队需要控制回答质量并能随产品更新快速迭代。

流程：供应商明确将一名 FDE（Forward Deployed Engineer，前线部署工程师）嵌入项目，与客户体验负责人反复配置和每周调整网站助手。

落地程度：已上线；客户官网截至检索日仍列出 Voltère。只确认客服咨询流程，不代表充电网络整体自动化。

人工职责：客户官网保留一般联系渠道；充电桩紧急情况仍拨打桩上号码，由24小时人工团队处理。

证据说明：供应商明确将一名 FDE（Forward Deployed Engineer，前线部署工程师）嵌入项目，与客户体验负责人反复配置和每周调整网站助手。

可切入环节：先做“会员卡、App、收费规则”的只读问答；测成功解决率和7天重复联系率，再考虑执行动作。

- 效率与使用规模：上线60天后的对比：有互动的网站会话中，联系表单提交率由1.28%降至0.99%，下降0.29个百分点。供应商估计2024年12月避免557次人工联系。。口径：客户或供应商自报；详见口径限制

- 成本变化：未公布部署费、运营费、每次成功解决成本或净现金节约；客户有“降低成本”的定性反馈。。口径：未披露项目总投入和净节省

### 介入前的问题与基线

- 【公开披露】电动车增长带来重复咨询，人工响应滞后，团队担忧支持量无法随充电需求扩张；要求可控制答案质量而非直接部署通用机器人。 [来源1](https://www.expertise.ai/live/case-studies/circuit-electric)

### 工程师具体做了什么

- 【公开披露】Expertise AI明确派FDE嵌入，工程师Ammar与客户体验负责人Félix共同迭代配置，每周调整；管理界面允许客户随产品服务更新重新训练助手。 [来源1](https://www.expertise.ai/live/case-studies/circuit-electric)

### 技术方案与数据流程

- 【公开披露】Voltère是网站问答助手，项目证据未证明语音部署；公开支持流程仍列帮助中心、虚拟助手及紧急充电站24小时人工电话。不能把供应商Voice AI菜单当本项目能力。 [来源1](https://www.expertise.ai/live/case-studies/circuit-electric) [来源2](https://www.lecircuitelectrique.com/nous-joindre)

- 【分析／复现建议】复现建议，非客户已公开实现：整理产品/收费/站点常见问题的版本化知识源；对紧急故障明确引导人工热线，评测旧政策、未知问题及无来源回答。

- 【分析／复现建议】复现建议，非客户已公开实现：用有互动会话为统一分母，并追踪其他渠道转移及重复联系；表单减少只有与成功解决和满意度合看才能说明用户获益。

### 解决程度与业务提升

- 【公开披露】上线60天后，互动会话表单联系率1.28%→0.99%，少0.29个百分点；原文称22.35%相对下降，但按展示值计算约22.66%，且标题另称30%。保留原始基数避免混用。2024年12月避免557次人工联系为供应商估计。 [来源1](https://www.expertise.ai/live/case-studies/circuit-electric)

### 尚未公开的信息

- 【未披露】模型、检索库、后台接口、训练含义、实际数据保留及自动转人工实现未披露。

- 【未披露】百分比不一致原因、会话量、因果对照、557估算公式、正确解决率与净成本未披露。

### 关键技能
- 知识库版本、法英双语评测、引用和拒答、人工转接、按会话/联系人去重埋点。

### 风险
- 错误充电操作或故障建议会影响安全；不能让助手屏蔽紧急人工渠道。

### 限制
- 同页标题30%、正文22.35%相互不一致；用展示的四舍五入率复算约22.66%相对下降。联系减少不等于问题已解决，未见重复来电/弃用率/独立审计。

### 来源
1. [供应商项目案例与工程师参与证据](https://www.expertise.ai/live/case-studies/circuit-electric)
2. [客户官网：Voltère与24小时人工急救服务](https://www.lecircuitelectrique.com/nous-joindre)
3. [Hydro-Québec官方：网络身份与业务](https://www.hydroquebec.com/transportation-electrification/faq.html)
4. [Hydro-Québec官方：总部位置](https://www.hydroquebec.com/renovations-head-office/)

## 71. 乌克兰经济部 / 国家就业服务局：就业服务热线语音受理

国家：乌克兰；项目落地：乌克兰
行业：公共就业服务
国家口径：主体为乌克兰经济部及国家就业服务局，官方供应商项目页明确说明已在该国国家就业热线投产，并使用乌克兰语；国家与落地范围均由本项目原文确认。

概述：人工热线有排队、非工作时间缺口，空袭警报时工作人员需避险，服务会中断。

流程：官方明确 FDE（Forward Deployed Engineer，前线部署工程师）与乌克兰团队共同落地；热线用自然乌克兰语回答一般咨询，转接前检查坐席可用性并生成摘要。

落地程度：生产环境中的有限范围试点；前80天处理2,698通，约占总量25%。不可把整个政府体系称为已自动化。

人工职责：复杂个案转人工。系统不能读取公民个案文件，也不报付款状态或申请细节。

证据说明：官方明确 FDE（Forward Deployed Engineer，前线部署工程师）与乌克兰团队共同落地；热线用自然乌克兰语回答一般咨询，转接前检查坐席可用性并生成摘要。

可切入环节：从公共流程、材料清单、办公时间问答开始；把等待时间、正确转接率和事实错误分开验收。

- 效率与使用规模：平均接听等待30–40秒降到18秒，按端点算缩短40%–55%。供应商称事实错误率低于2%、约20%常规问题端到端处理；后者分母及抽样方法不清。。口径：客户或供应商自报；详见口径限制

- 成本变化：未公布投入、通话运营成本、编制变化或净节省。。口径：未披露项目总投入和净节省

### 介入前的问题与基线

- 【公开披露】原热线有固定菜单和等待，非工作时段来电无人接；空袭警报时人工需入避难所。上线前平均接听等待30–40秒。 [来源1](https://elevenlabs.io/blog/ukraines-employment-services)

### 工程师具体做了什么

- 【公开披露】ElevenLabs FDE与乌克兰团队并肩部署；经济部将ElevenAgents接入国家就业服务联络中心，属于Obrii劳动力市场生态的一部分，文章作者亦为政府部署FDE。 [来源1](https://elevenlabs.io/blog/ukraines-employment-services)

### 技术方案与数据流程

- 【公开披露】代理以乌克兰语24小时回答一般问题；空袭期间承担全部流量，转人工前检查坐席是否可用，转接附AI摘要。无公民个案档案访问权，不读取付款状态或申请详情，个案审查由人工负责。 [来源1](https://elevenlabs.io/blog/ukraines-employment-services)

- 【分析／复现建议】复现建议，非客户已公开实现：用噪声、压缩电话音频和口音测试意图识别；模拟警报开始/结束、坐席瞬时离线及重复转接，确保可用性检查与实际交接一致。

### 解决程度与业务提升

- 【公开披露】前80天处理2698通，约总量25%；平均等候降至18秒，报告事实错误低于2%、约20%常规问题端到端完成，未公开抽样及分母。非工作时段来电超过总量20%，与20%常规解决是不同指标；月8万通为未来预测。 [来源1](https://elevenlabs.io/blog/ukraines-employment-services)

### 尚未公开的信息

- 【未披露】知识来源、模型版本、电话平台、坐席状态接口、摘要脱敏与保存期限未披露。

- 【未披露】错误率判定/样本、转接成功计数、常规解决分母、成本、编制影响及净收益未披露。

### 关键技能
- 方言与电话音频评测、可用性探测、摘要转接、服务中断降级、隐私分级与只读知识库。

### 风险
- 就业服务的错误信息可能影响权益；案例回避个案读取，入企服务不能擅自扩展到资格或福利决定。

### 限制
- 前80天数据，不代表长期表现；预计8万通/月是未来负荷，不能计作已实现规模。

### 来源
1. [ElevenLabs官方：明确工程师合作、生产部署和80天数据](https://elevenlabs.io/blog/ukraines-employment-services)

## 72. Itaú Unibanco：COBOL企业税号字段改造

国家：巴西；项目落地：巴西
行业：商业银行
国家口径：Itaú官方投资者关系页列巴西圣保罗主体地址；案例为该银行巴西企业税号CNPJ改造，按此项目业务国家列巴西。

概述：旧COBOL系统存在多种税号字段表达，需要将数字字段扩展为字母数字格式。

流程：银行专家追踪运行时数据流、识别约20种字段变体，将列宽等约束编入操作手册；Devin并行修改。

落地程度：官方称数百程序改造已完成，较政府期限提前3个月。

人工职责：银行COBOL专家定义约束和数据流；逐PR审批和上线审核细则未披露。

证据说明：Jia Wu的前线部署工程师（Forward Deployed Engineer）演讲14:35后展示Itaú税号迁移案例；Cognition官方工程文章交叉确认同项COBOL税号改造。

可切入环节：分析：从有明确输入输出的批处理或小范围重构切入。

- 完成进度：提前3个月。口径：相对规定期限，不是比人工基线快3个月。

- 生产错误：报告为0。口径：供应商报告；监测期与错误定义未知，不代表永不出错。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】监管要求企业税号支持字母数字，而COBOL字段有约20种表达。普通代理容易破坏72列限制和COMP类型，需银行主机专家先追踪运行时数据流。 [来源1](https://cognition.com/blog/how-devin-is-modernizing-cobol-at-fortune-500-companies)

### 工程师具体做了什么

- 【公开披露】将专家发现的字段命名、列宽及类型约束编码为操作手册，再用并行代理执行数百程序的重复重构。 [来源1](https://cognition.com/blog/how-devin-is-modernizing-cobol-at-fortune-500-companies)

- 【公开披露】部署负责人演讲将该项目作为FDE（Forward Deployed Engineer，前线部署工程师）实践，报告减少一半以上工程时间；不把另一家银行或匿名客户数字移入本案。 [来源2](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)

### 技术方案与数据流程

- 【公开披露】本案是字段扩展与跨程序一致性修改，不是把实时交易系统完整迁移到新架构。 [来源1](https://cognition.com/blog/how-devin-is-modernizing-cobol-at-fortune-500-companies)

- 【公开披露】同银行更广泛部署包括CI/CD安全扫描后生成补丁交人审核、Wiki/Search代码知识、人工给测试操作手册后审查测试。这些是组织背景，不证明税号项目使用相同流水线。 [来源4](https://devin.ai/customers/itau)

- 【分析／复现建议】复现建议，非客户已公开实现：测试应覆盖字段读写、格式校验、上下游接口、历史数据与回退；以生产语义正确性而非代码生成量验收。

### 解决程度与业务提升

- 【公开披露】供应商称提前监管期限3个月完成，生产错误为0；观察窗口和错误口径未公开。 [来源1](https://cognition.com/blog/how-devin-is-modernizing-cobol-at-fortune-500-companies)

- 【公开披露】银行全范围20—30%吞吐提升、10—15%周期下降，以及.NET迁移5倍成本改善属于其他范围，不能归因本税号改造。 [来源4](https://devin.ai/customers/itau)

### 尚未公开的信息

- 【未披露】税号项目模型版本、测试规模、审核门禁、部署批次、回滚流程、费用与净节省未披露。

### 关键技能
- 分析：COBOL布局与跨程序数据流
- 分析：回归测试及领域约束编码

### 风险
- 分析：字段偏移误判可影响交易
- 分析：主机与代理测试环境差异

### 限制
- 未将同一银行.NET、SQL迁移拆为多个前线部署工程师（Forward Deployed Engineer）案例。
- 不把此项字段重构扩张为完全自主实时交易系统迁移。

### 来源
1. [How Devin Is Modernizing COBOL at Fortune 500 Companies](https://cognition.com/blog/how-devin-is-modernizing-cobol-at-fortune-500-companies)
2. [Jia Wu：How Forward Deployed Engineering is done at Cognition](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)
3. [Itaú Unibanco Investor Relations](https://www.itau.com.br/relacoes-com-investidores/en/itau-unibanco/?selectedTab=3)
4. [Itaú customer case](https://devin.ai/customers/itau)

## 73. Bilt：产品开发与运维编码代理

国家：美国；项目落地：未披露
行业：住房支付与会员奖励平台
国家口径：Bilt官方公告明确纽约总部，美国；本项工程组织部署国家未单独披露。

概述：工程团队需要跨代码库开发、维护与运维排障支持。

流程：Devin处理Java升级、GCP日志调查与修复初稿、Figma转前端初稿和代码变更摘要；工程师迭代实现。

落地程度：2024年12月设计伙伴试用，2025年2月推广到工程组织；案例观察期已产生合并PR。

人工职责：工程师审核并决定接受PR，复杂任务继续人工迭代；具体生产发布审批未知。

证据说明：Cognition部署工程负责人Jia Wu在前线部署工程师（Forward Deployed Engineer）演讲15:13逐项讨论Bilt工程交付；官方案例交叉确认设计伙伴及组织上线过程。

可切入环节：分析：从低风险维护任务及修复建议入手，保留人工合并和发布。

- PR接受率：超过50%。口径：案例观察期，具体分母定义与日期未知；不是代码正确率。

- 每周PR：平均117个。口径：案例所述最近30天；非当前实时数值，不能推为全部前线部署工程师（Forward Deployed Engineer）净增贡献。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】团队希望把重复开发、日志排障和前端原型工作交给代理；没有统一人工工时基线。2024年12月从少量工程师试点，2025年2月扩至组织。 [来源1](https://devin.ai/customers/bilt)

### 工程师具体做了什么

- 【公开披露】部署负责人以Bilt解释交付、接受率与工程容量的区别；10名工程师等效产出是估算，不是裁员或精确节省工资。 [来源2](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)

### 技术方案与数据流程

- 【公开披露】用GCP排障操作手册规范读日志、找原因、提修复；连接Figma API取组件与变量，结合自有组件库做前端MVP，另用于Java升级和代码摘要。 [来源1](https://devin.ai/customers/bilt)

- 【公开披露】需求清楚的任务由代理实施；复杂任务先生成初稿，再由工程师在IDE调整。逐项自动部署权限与生产审批未披露。 [来源1](https://devin.ai/customers/bilt)

- 【分析／复现建议】复现建议，非客户已公开实现：按任务难度分层，分别记录PR接受率、合并耗时、返工、缺陷、审核时间和交付价值；避免把PR数量直接换算成本。

### 解决程度与业务提升

- 【公开披露】官方称106名工程师中超过一半周活；自2月800+PR，报道时最近30天平均117 PR/周，接受率超过50%。数字是文章观察窗，不能当当前实时值。 [来源1](https://devin.ai/customers/bilt)

### 尚未公开的信息

- 【未披露】完整时间序列、接受率分母、PR难度、对照组、订阅/部署投入、生产缺陷和净ROI未公开。

### 关键技能
- 分析：跨仓库上下文与任务验收
- 分析：运维日志权限隔离

### 风险
- 分析：代码或日志暴露
- 分析：PR数量掩盖维护成本

### 限制
- 与Bilt/Decagon金融客服是不同业务项目和供应商，单独记录软件工程部署。
- 不将估算10名工程师等效产出解释为裁减10人或前线部署工程师（Forward Deployed Engineer）独立因果收益。

### 来源
1. [Bilt engineering with Devin](https://devin.ai/customers/bilt)
2. [Jia Wu：How Forward Deployed Engineering is done at Cognition](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)
3. [Bilt New York headquarters](https://newsroom.biltrewards.com/bilt-announces-new-headquarters-in-new-york-citys-meatpacking-district)

## 74. Cognition：Devin长程编码代理模型集成

国家：美国；项目落地：未披露
行业：软件开发自动化平台
国家口径：Cognition官方About说明总部San Francisco；该Anthropic集成工程发生地未公布，因此不按总部补项目国家。

概述：自主编码代理容易偏离需求、在长上下文中失去任务一致性。

流程：围绕Devin集成Claude，调整工具、上下文、轨迹监控和防护；用编辑、定位文件与端到端测试验证新模型后进入生产。

落地程度：已进入Devin生产工作流；原文称新模型通过评测后通常首日替换上线。

人工职责：用户确定任务与高层取舍；代理提供PR与运行视频供人检查；并非所有客户均全自动合并。

证据说明：Anthropic官方Problem Solvers明确受访者与深入嵌入工作的Anthropic工程师对谈；Cognition官方客户访谈进一步明确Anthropic派工程师共同试新能力，并把客户样例反馈到后续模型。该组合支持项目特定嵌入共建，未声称人员均有前线部署工程师（Forward Deployed Engineer）正式职称。 同义职责证据，非原前线部署工程师职位名。

可切入环节：先在隔离代码库验证明确工单，用测试和人工合并门槛控制风险。

- 采用变化：Devin使用量至少7倍。口径：客户称自前一年末以来；具体截止日未标，不能归因于Anthropic驻场单一因素。

- 嵌入团队结果：未单独量化。口径：业务指标与模型整体改善不能直接作为前线部署工程师（Forward Deployed Engineer）因果效果。

- 成本：未公开。口径：无集成项目全成本。

### 介入前的问题与基线

- 【公开披露】长任务易丢失上下文，用户意图常不充分，成功率波动。换基础模型会改变整个代理行为，不能只替换一个API名称。 [来源2](https://claude.com/customers/cognition)

### 工程师具体做了什么

- 【公开披露】Anthropic工程师与Cognition紧密共同测试、复盘失败例，把结果反馈给未来模型。原文未逐人确认FDE（Forward Deployed Engineer，前线部署工程师）职称。 [来源1](https://claude.com/problem-solvers) [来源2](https://claude.com/customers/cognition)

### 技术方案与数据流程

- 【公开披露】代理在预备代码和依赖的VM中使用文件、提交记录及PR信息；集成需调整模型路由、提示词、工具定义、上下文管理、轨迹监控与护栏。 [来源2](https://claude.com/customers/cognition)

- 【公开披露】评测覆盖原子文件修改、定位代码和端到端任务。新模型必须整体改善且无重要回归才上线；50—70人是Cognition参与工程师，不能写成供应商驻场人数。 [来源2](https://claude.com/customers/cognition)

- 【分析／复现建议】复现建议，非客户已公开实现：保存版本化评测、模型与提示词配置；对高风险命令限制权限，设差异审查、失败重试上限和旧模型回退。

### 解决程度与业务提升

- 【公开披露】供应商案例报告某次Claude采用后每周合并PR增至3.5倍；没有足够控制组证明全部由模型或嵌入工程师造成。 [来源2](https://claude.com/customers/cognition)

### 尚未公开的信息

- 【未披露】完整评测集、模型路由策略、各版本回归门槛、成本明细和用户业务收益未公开；原页模型版本表述存在疑点，不据此补写版本。

### 关键技能
- 模型替换回归评测
- 工具接口适配
- 长程轨迹监控
- 用户反馈回流

### 风险
- 长任务偏航
- 错误代码和不安全工具调用

### 限制
- 未披露驻场持续时长、地点及工程师人数。
- 原文3.5倍PR指标搭配Sonnet 3.6名称存在疑点，本条不采用该指标。
- 不把Cognition下游Goldman、Mercedes、US Army的使用各自当作Anthropic 前线部署工程师（Forward Deployed Engineer）案例。

### 来源
1. [Anthropic官方嵌入工程师系列](https://claude.com/problem-solvers)
2. [Cognition负责人官方客户访谈](https://claude.com/customers/cognition)
3. [Cognition官方总部](https://cognition.com/about)

## 75. NBA：实时比赛事件检测最小可用产品

国家：美国；项目落地：未披露
行业：职业篮球赛事与体育数据服务
国家口径：主体国家为美国；来源：NBA官方总部说明，正文明确NBA总部位于纽约曼哈顿。项目实际落地国家未单独披露，不以总部推断。

概述：NBA需要把比赛中的实时事件识别转为可运行的系统。

流程：AWS负责人披露团队从启动到部署实时事件检测MVP。公开材料未给出该MVP的完整数据管道和模型架构，不把其他NBA产品功能拼接进来。

落地程度：已部署最小可用产品（Minimum Viable Product，MVP）；不扩大表述为全联盟全部产品正式生产。

人工职责：AWS工程师参与客户日常工程交付；NBA人员提出业务需求。该MVP具体人工校验和审批机制未披露。

证据说明：B组合：AWS官方公告点名NBA是已嵌入前线部署工程师（Forward Deployed Engineer）的客户；负责该组织的Taimur Rashid在宣布前线部署工程师（Forward Deployed Engineer）的本人帖子中把进入客户工程流程的团队与NBA实时事件检测12周部署MVP明确关联。未把普通NBA云合作故事当作项目证据。

可切入环节：分析建议：围绕一种可验证比赛事件构建影子评测，再决定上线范围。

- MVP交付周期：12周。口径：AWS负责人的项目级一手帖子明确称从kickoff到deployed MVP。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】需要把实时赛事事件识别从想法推进到可部署原型；人工识别耗时、历史错误率与原系统未披露。 [来源1](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ)

### 工程师具体做了什么

- 【公开披露】AWS负责人描述团队进入客户站会、代码库并共同交付；官方新增投资公告明确NBA属于已嵌入团队的客户。 [来源1](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ) [来源2](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers)

### 技术方案与数据流程

- 【公开披露】已公开的是实时事件检测MVP及交付周期，没有公布本项目视频输入、传感器、模型、事件标签或数据存储架构。 [来源1](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ)

- 【分析／复现建议】复现建议，非客户已公开实现：先定义事件分类和金标准，分开评估事件级准确率、漏报、时延及人工确认；直播业务还需异常降级与人工回退。

### 解决程度与业务提升

- 【公开披露】负责人报告12周从启动到部署MVP；这是交付时间，不是已证明赛场全量生产覆盖或12周投资回收。 [来源1](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ)

### 尚未公开的信息

- 【未披露】数据流、具体AWS服务、模型、评测结果、上线规模、人工确认、成本和节省值未披露。

### 关键技能
- 分析：实时事件标签和评测口径
- 分析：流式数据延迟预算
- 分析：与客户代码库及发布流程协作

### 风险
- 分析：误检漏检
- 分析：MVP与全量生产范围混淆
- 分析：比赛数据授权

### 限制
- 主要项目细节来自组织负责人的一手公开帖子，缺少客户独立复核。
- 不推断该MVP与NBA Inside the Game全部功能为同一部署。

### 来源
1. [AWS Forward Deployed Engineering: A Dedicated Organization with $1B Investment](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ)
2. [AWS invests $1 billion to embed AI forward deployed engineers with customers](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers)
3. [AWS doubles investment in AWS Generative AI Innovation Center](https://aws.amazon.com/blogs/machine-learning/aws-doubles-investment-in-aws-generative-ai-innovation-center-marking-two-years-of-customer-success/)
4. [NBA官方总部说明](https://pr.nba.com/nba-2k-league-all-star-comes-to-new-york-city/)

## 76. Jabil（捷普）：Jabil制造车间故障排查知识助手

国家：美国；项目落地：未披露
行业：电子制造服务与工业供应链
国家口径：主体国家为美国；来源：AWS Jabil官方客户故事，Opportunity明确总部St. Petersburg, Florida。项目实际落地国家未单独披露，不以总部推断。

概述：Jabil车间员工需要跨语言查找制造规范和故障排查资料。

流程：基于Amazon Q Business建立车间助手，首版后继续整合文档、事件工单和知识文章，供操作员查询诊断依据。

落地程度：已上线供全球员工使用；覆盖哪些国家和多少工厂未明确。

人工职责：员工利用回答排查问题；来源未说明自动控制生产设备，也未披露逐条人工审批。

证据说明：B组合：客户故事明确GenAIIC顾问参与车间助手且首版后持续集成数据；该交付组织负责人Taimur Rashid在宣布前线部署工程师（Forward Deployed Engineer）的本人帖子中，说明工程师进入客户代码库和日常工程流程，并逐项目点名Jabil智能车间助手一周首版。属于有一手项目绑定的嵌入式交付，不把所有创新中心咨询自动改称前线部署工程师（Forward Deployed Engineer）。

可切入环节：分析建议：先选非安全关键设备的只读排障知识，保留原文链接并让操作员确认。

- 首版构建周期：1周。口径：AWS客户故事Outcome及组织负责人帖子相互吻合；不是完整全球 rollout 周期。

- 知识覆盖：超过1,700份资料。口径：上线后可查询政策、制造规范和排障文档。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】全球制造信息散在系统与文档，员工需跨语言查找政策、制造规范和排障知识。现代化还涉及100家工厂与400个应用，但不是助手单独规模。 [来源1](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)

### 工程师具体做了什么

- 【公开披露】AWS Generative AI Innovation Center顾问与Jabil用Amazon Q Business合作，首轮助手1周完成，后续数周补文档、工单和知识文章。正式个人FDE（Forward Deployed Engineer，前线部署工程师）头衔未公开。 [来源1](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)

### 技术方案与数据流程

- 【公开披露】检索知识覆盖约1700份政策/制造/排障文档，支持全球员工多语言提问。正文没有给切块、向量库、模型版本及回答引用结构。 [来源1](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)

- 【分析／复现建议】复现建议，非客户已公开实现：接入时保留原文档访问权限；按语言、岗位和故障类型测试正确率与来源可追溯性，危险维修建议应交合格人员核验。

### 解决程度与业务提升

- 【公开披露】助手改善排障与信息获取是定性披露。67—83%部署提速和74%处理改善属于EBA及基础设施工作；23%成本下降属于Glue Flex Data Dispatcher，不是助手节省。 [来源1](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)

### 尚未公开的信息

- 【未披露】助手回答准确率、节时基线、实际月活、订阅和实施费、生产质量与净收益未公开。

### 关键技能
- 分析：多源制造知识接入
- 分析：多语言检索评价
- 分析：持续数据源集成与运维

### 风险
- 分析：过期工艺信息
- 分析：错误诊断影响生产安全
- 分析：跨站点访问权限

### 限制
- 67–83%部署提速、74%数据处理提速属于同一客户的基础设施/EBA改造，不能归因于车间AI助手，故未作为本例效益。
- 100多个站点是公司运营规模，不代表助手已逐站部署。
- 客户故事仍称GenAIIC顾问；前线部署工程师（Forward Deployed Engineer）关联来自后来的一手负责人说明。

### 来源
1. [Jabil Collaborates with AWS to Drive Manufacturing Efficiency and Process Optimization](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)
2. [AWS Forward Deployed Engineering: A Dedicated Organization with $1B Investment](https://www.linkedin.com/posts/taimurrashid_aws-invests-1-billion-to-embed-ai-forward-activity-7477785579259150336-EXoQ)
3. [AWS doubles investment in AWS Generative AI Innovation Center](https://aws.amazon.com/blogs/machine-learning/aws-doubles-investment-in-aws-generative-ai-innovation-center-marking-two-years-of-customer-success/)
4. [AWS Jabil官方客户故事](https://aws.amazon.com/solutions/case-studies/jabil-manufacturing-transformation-generative-ai/)

## 77. CMA CGM：货运放行、单证与客服辅助

国家：法国；项目落地：法国
行业：集装箱海运与综合物流
国家口径：主体国家为法国：CMA CGM官方Legal Conditions列明总部在Marseille, France。项目地法国来自客户AI NOW原文工程师已加入马赛和Grand Central现场团队；全球业务覆盖不据此扩展项目落地国家。

概述：货运客户查询、单证与放行涉及多系统、大量运营信息。

流程：共同开发连接业务知识与内部应用的代理，协助货物放行、处理海运单证和客户信息请求；复杂客户问题升级给人工。

落地程度：客户2026年5月材料回顾已部署的海运、物流和媒体方案；MAIA Powered by Mistral自6月1日起渐进推广为当时计划，80,000名员工是设计覆盖范围。

人工职责：复杂客户事项转人工；货物最终放行审批细节未公开。

证据说明：客户官方确认约20名Mistral工程师已加入Marseille及CMA Media团队；供应商项目页具体确认货物放行、客户信息请求和海运文档处理。是已嵌入一线的部署工程职责，未将其头衔硬写成前线部署工程师（Forward Deployed Engineer）。 同义职责证据，非原前线部署工程师职位名。

可切入环节：先从单证完整性与客户状态只读查询开始，异常交运营人员。

- 驻场团队：约20名工程师。口径：客户明确已经加入Marseille及CMA Media团队；这是交付投入，不是业务收益。

- 项目节时与成本：未披露可单独归因值。口径：集团55+ AI项目、每年5,400万查询量和200个用例不能全归给Mistral本项目。

### 介入前的问题与基线

- 【公开披露】客户信息请求量大，货物放行、航运单证和业务知识跨系统；集团年5400万请求是总需求量，不是AI已经处理量。 [来源1](https://www.cmacgm-group.com/en/news-media/ai-now-summit-ai-deployment-across-cma-cgm-group-operations)

### 工程师具体做了什么

- 【公开披露】客户称约20名Mistral工程师已加入马赛及媒体现场团队，五年合作从2025年4月开始；属于嵌入式交付职责，非已核实个人职称。 [来源1](https://www.cmacgm-group.com/en/news-media/ai-now-summit-ai-deployment-across-cma-cgm-group-operations)

### 技术方案与数据流程

- 【公开披露】共同工具涉及单证、货物放行辅助、客户信息答复和媒体事实核查；供应商只确认功能层，没有公开完整实现。 [来源2](https://mistral.ai/customers/cma-cgm/)

- 【公开披露】MAIA连接内部应用和业务知识，6月1日起渐进推广、设计覆盖80000人是当时计划；复杂客服交人工。集团其他供应商项目不可并入同一交付。 [来源1](https://www.cmacgm-group.com/en/news-media/ai-now-summit-ai-deployment-across-cma-cgm-group-operations)

- 【分析／复现建议】复现建议，非客户已公开实现：单证抽取与校验、检索答复和实际放行权限应分离；对不可逆业务动作保留授权与复核，并记录每次取证来源。

### 解决程度与业务提升

- 【公开披露】客户强调响应质量与运营提升，但55个AI项目、200个用例是集团组合，不是Mistral单案效果。 [来源1](https://www.cmacgm-group.com/en/news-media/ai-now-summit-ai-deployment-across-cma-cgm-group-operations)

### 尚未公开的信息

- 【未披露】模型版本、文档解析和校验规则、系统接口、放行审批、准确率、事故率、单案成本及量化效率未披露。

### 关键技能
- 航运单证处理
- 业务系统连接
- 权限与放行审批
- 客服升级

### 风险
- 错误放行可能造成财产损失
- 跨业务AI总量与本项目归因混淆

### 限制
- 正式前线部署工程师（Forward Deployed Engineer）职称未披露，证据B表示项目特定的一线嵌入职责。
- 不把媒体事实核查拆成第二个独立客户案例。
- 客户公告描述集团多家AI供应商并存，整体效益不得全归因Mistral。

### 来源
1. [客户官方：工程师已加入现场团队及已部署方案](https://www.cmacgm-group.com/en/news-media/ai-now-summit-ai-deployment-across-cma-cgm-group-operations)
2. [Mistral逐项目案例](https://mistral.ai/customers/cma-cgm/)
3. [CMA CGM官方法定信息及总部](https://www.cmacgm-group.com/en/legal-terms)

## 78. HTX（新加坡内政科技局）：公共安全本地模型与内部平台

国家：新加坡；项目落地：新加坡
行业：公共安全科技与政府信息基础设施
国家口径：供应商和HTX政府官网均明确为新加坡内政部科技机构，并在HTX自有NGINE内部部署；不是从供应商总部推断。

概述：通用模型缺少新加坡法律、语言和业务术语，敏感任务需要隔离网内部运行。

流程：双方工程和研究能力进入HTX训练、数据、评测与产品交付流程，训练Phoenix并在内部NGINE支持文档分类、问答和信息摘要。

落地程度：Phoenix Small/Medium已部署在NGINE；客户确认本地模型和内部基础设施投入使用。机器人等后续领域属于扩展研究，不冒充全部生产。

人工职责：公共安全人员使用辅助结果；HTX保有模型、基础设施和知识控制。公开材料未列所有具体人审闸门。

证据说明：Mistral逐项目官方页明确embedded AI expertise，列研究科学家、AI工程及HTX产品化实践；结合客户官网已上线Phoenix及NGINE说明。不是从Forge客户名单推定前线部署工程师（Forward Deployed Engineer）。 同义职责证据，非原前线部署工程师职位名。

可切入环节：从非执法决定的内部文档检索和摘要切入，保留来源与人工判断。

- 已部署形态：本地NGINE上的Phoenix模型与工程平台。口径：官方明确内部部署；未披露活跃人员数和处理量。

- 效率与成本：未公开可审计量化结果。口径：官方定性称提升人员生产率；参数数和基准表现不等于运行节省。

### 介入前的问题与基线

- 【公开披露】新加坡公共安全需要本地语言、法律语境和可控数据环境，通用模型与联网部署不能覆盖所有要求。 [来源1](https://mistral.ai/customers/htx/)

### 工程师具体做了什么

- 【公开披露】Mistral研究工程师与HTX团队共建Phoenix；从2025年3月合作，支持本地权重及隔离环境。 [来源1](https://mistral.ai/customers/htx/)

### 技术方案与数据流程

- 【公开披露】官方介绍用Forge/Studio适配模型，在NGINE提供Phoenix Small/Medium用于摘要、分类与聊天。 [来源1](https://mistral.ai/customers/htx/)

- 【公开披露】相关联合论文披露Phoenix-VL 1.5 Medium：123B语言模型加视觉模块，本地继续训练及上下文扩展，再做监督/偏好优化；数据去重、基准去污染并用人工本地标注。论文模型不能自动等同所有NGINE版本。 [来源4](https://arxiv.org/pdf/2605.10391)

- 【公开披露】论文给出vLLM在B200 BF16的推理基准、并行与并发取舍；这是公开技术评测，不是所有生产集群的实际配置。 [来源4](https://arxiv.org/pdf/2605.10391)

- 【分析／复现建议】复现建议，非客户已公开实现：将公共安全业务的人工决定权限与模型实验指标分开管理；只在批准的用途、数据和网络边界内上线。

### 解决程度与业务提升

- 【公开披露】联合论文新加坡政府知识分数0.8366→0.9265为零样本pass@1基准；不表示公共安全成效提高同一比例。安全测试仍有提示注入/泄露失败。 [来源4](https://arxiv.org/pdf/2605.10391)

### 尚未公开的信息

- 【未披露】实际执法使用规模、人工签批规则、生产差错、经济成本与业务效率未公开；实验安全分数不保证安全。

### 关键技能
- 隔离网模型部署
- 领域训练与评测
- 本地语言安全基准
- 知识转移

### 风险
- 公共安全误判具有高后果
- 数据控制不等于所有用途自动合规

### 限制
- 正式前线部署工程师（Forward Deployed Engineer）职称未披露；B依据逐项目嵌入工程能力与实际内网部署组合。
- 边境和网络安全是用途示例，未提供各独立产品上线清单。

### 来源
1. [Mistral官方HTX案例](https://mistral.ai/customers/htx/)
2. [HTX官方合作扩展](https://www.htx.gov.sg/whats-happening/all-news---events/all-news/2025/htx-expands-partnership-with-mistral-ai)
3. [HTX官方：主权AI实际架构](https://www.htx.gov.sg/whats-happening/all-news---events/all-news/2026/why-sovereign-ai-is-key-to-scaling-public-safety-impact)
4. [HTX与Mistral联合论文：Phoenix-VL 1.5 Medium Technical Report](https://arxiv.org/pdf/2605.10391)

## 79. BBVA：银行员工知识与工作流共建

国家：西班牙；项目落地：未披露
行业：商业银行与零售金融
国家口径：BBVA官方审慎监管披露明确西班牙银行主体及Bilbao注册地址；项目扩展称25国，未给完整实际部署国家名单。

概述：分散的银行知识和重复文书任务拖慢员工工作。

流程：从员工ChatGPT Enterprise和定制GPT开始，围绕知识、内部协作及银行核心流程联合设计AI工作方式。

落地程度：2024年5月先向3,300员工推广，后扩至11,000；120,000员工、25国为扩大合作覆盖计划，不能当全部已活跃。

人工职责：员工制作和使用定制GPT；是否每个输出有强制复核未披露。

证据说明：OpenAI Deployment Company（OpenAI部署公司）官网在Forward Deployed Engineering（前线部署工程）专页的Case studies区逐项列BBVA员工工作流；同一银行部署的规模与采用率由OpenAI客户公告支持，不将结果单独归因于工程师模式。

可切入环节：先做有来源的内部制度检索，由员工确认后使用。

- 节时：每周接近3小时。口径：员工常规任务自报；未披露独立对照、样本和净成本。

- 日使用：超过80%。口径：对应早期11,000员工推广阶段，不是全集团120,000员工。

- 成本：未公开。口径：无全成本和净收益。

### 介入前的问题与基线

- 【公开披露】银行希望减轻日常知识与文书任务，采用规模从2024年5月3300席增至11000席；不意味着所有任务已自动化。 [来源2](https://openai.com/index/bbva-collaboration-expansion/)

### 工程师具体做了什么

- 【公开披露】部署工程案例目录列BBVA；官方合作公告明确专门团队与OpenAI产品、研究和客户成功共同推进。目录的一般方法不作为该客户具体架构。 [来源1](https://deploy.co/) [来源2](https://openai.com/index/bbva-collaboration-expansion/)

### 技术方案与数据流程

- 【公开披露】ChatGPT Enterprise用于员工工作，形成数千自定义GPT；扩大合作包括接银行内部系统的代理和结构化培训。具体系统、权限传递与工具调用未公开。 [来源2](https://openai.com/index/bbva-collaboration-expansion/)

- 【分析／复现建议】复现建议，非客户已公开实现：先按数据敏感级别开放只读任务，区分回答建议与交易执行，建立审批、审计及越权/泄露评测。

### 解决程度与业务提升

- 【公开披露】2025年12月公告称11000人群体超过80%每日使用、日常任务平均每周节省近3小时，属客户报告。120000人/25国是扩展范围，不能当实际活跃量。 [来源2](https://openai.com/index/bbva-collaboration-expansion/)

### 尚未公开的信息

- 【未披露】采样和节时测量方法、按岗位表现、质量/风险结果、合同费和净成本未披露；客户面向消费者的Blue助手不能并入员工节时指标。

### 关键技能
- 银行流程发现
- 权限隔离
- 知识接入
- 真实样本评测

### 风险
- 银行数据泄露
- 员工采用率不能等同财务ROI

### 限制
- FDE页面对参与描述为整体合作；不能将所有自助GPT成果归为FDE单独效果。
- 全球扩展国家名单未逐项披露。

### 来源
1. [DeployCo FDE案例区](https://deploy.co/)
2. [BBVA合作扩展](https://openai.com/index/bbva-collaboration-expansion/)
3. [BBVA法定实体和注册地址](https://shareholdersandinvestors.bbva.com/microsites/pilarIII2015/en/1/cd.html)

## 80. Surf Air Mobility（Southern Airways／Mokulele自营航空运营）：SurfOS飞行、机组与燃油运营

国家：美国；项目落地：美国
行业：航空运输
国家口径：Surf Air Mobility官方品牌页说明主体位于洛杉矶；本例自营Southern Airways服务美国本土，Mokulele服务夏威夷，且两家均采用SurfOS。国家范围限这一本土及夏威夷自营运营案例，不外推到未来国际客户。

概述：航空运营的数据、调度、机组储备与燃油决策需要协同。

流程：SurfOS连接飞行运营、机组储备、燃油优化；BrokerOS处理飞机寻源、报价、运营商沟通；作为自营航空业务生产系统再扩展第三方。

落地程度：截至2026-10-07 flight management、crew reserve、fuel optimization模块已在自营航司部署。第三方OperatorOS合同不等于全部已上线，应与内部生产分开。

人工职责：仍由航空运营人员、飞行员、调度／经纪人使用系统；来源未提供人工审批矩阵或裁员人数，不能断言所有岗位保留。

证据说明：客户官方SurfOS材料第4页明确利用Palantir的 FDE（Forward Deployed Engineer，前线部署工程师）。参与证据针对SurfOS整体，成效来自另一期公司公告。

可切入环节：只读整合一支机队的航班与油耗异常，人工审核优化建议；先建立每飞行小时基线。

- 直接运营成本/飞行区段小时：下降6%。口径：2026年至公告日YTD改善；对照窗口未清楚定义，不改称同比。

- 燃油消耗/飞行区段小时：下降9%。口径：同一公司自报指标，非生成式模型单独效果。

- 飞行员成本/飞行区段小时：下降9%。口径：单位产出成本，并非飞行员工资下降9%。

- 劳动生产率/飞行区段小时：提高15%。口径：公司使用此口径；详细计算式与基期未披露。

- 项目净ROI：未知。口径：软件/服务存在股票支付；未提供扣除全部成本后的净节省。

### 介入前的问题与基线

- 【公开披露】区域航空/包机业务需要协调飞机、机组、维护、报价与订单。商业化材料把手工和传统调度作为目标痛点。 [来源1](https://s202.q4cdn.com/166167538/files/doc_presentations/2026/05/SurfOS-Go-To-Market.pdf)

### 工程师具体做了什么

- 【公开披露】客户投资者材料第4、12页明确Palantir FDE（Forward Deployed Engineer，前线部署工程师）和商业化/企业销售协作，基础为Foundry及AIP；不能把销售阶段意向客户说成已部署。 [来源1](https://s202.q4cdn.com/166167538/files/doc_presentations/2026/05/SurfOS-Go-To-Market.pdf)

### 技术方案与数据流程

- 【公开披露】材料第9页：自营航司机组值勤、飞行/乘客和维修记录，加包机报价成交及机源信息，经Foundry本体支持测试和部署代理。定价、机组、维护等为公开代理示例，未逐项证明已生产。 [来源1](https://s202.q4cdn.com/166167538/files/doc_presentations/2026/05/SurfOS-Go-To-Market.pdf)

- 【公开披露】2026年10月7日公司更新确认自营航司用航班管理、机组储备及燃油优化模块；完整工资、派遣、维修数字化仍为第四季度目标。 [来源3](https://markets.financialcontent.com/stocks/article/bizwire-2026-10-7-surf-air-mobility-provides-airline-operations-business-update-highlighting-surfos-driven-efficiency-and-electric-aviation-priorities-in-hawaii?Language=english%2F1000)

- 【分析／复现建议】复现建议，非客户已公开实现：机组排班需以值勤和资质硬约束验收，优化器输出须可解释并支持人工覆盖；不能让语言模型独立作安全放行决定。

### 解决程度与业务提升

- 【公开披露】公司称2026年迄今每block hour直接成本下降6%、燃油成本下降9%、飞行员成本下降9%、劳动生产率提高15%。同期机队、航线和管理调整并行，不能全归因FDE。 [来源3](https://markets.financialcontent.com/stocks/article/bizwire-2026-10-7-surf-air-mobility-provides-airline-operations-business-update-highlighting-surfos-driven-efficiency-and-electric-aviation-priorities-in-hawaii?Language=english%2F1000)

- 【公开披露】5月材料另报BrokerOS 2026Q1对2025Q1：头部经纪预订+32%、报价到成交更快57%、平台处理支付+40%，属管理层估计，与航空运营指标分开。 [来源1](https://s202.q4cdn.com/166167538/files/doc_presentations/2026/05/SurfOS-Go-To-Market.pdf)

### 尚未公开的信息

- 【未披露】具体模型、优化算法、API、评测、人工审批、故障回退、软件实施费与完整净ROI未披露；外部客户商业化目标不等于已签约收入。

### 关键技能
- 运行数据与时序接入
- 约束优化及调度
- 燃油/工时单位口径
- 安全边界、审计和变更控制

### 风险
- 不能让无约束生成模型直接决定飞行安全动作
- 同时存在航线、机队及管理变化，归因须谨慎

### 限制
- AI-enabled不证明每个优化步骤都是LLM
- 内部航空生产改善不应冒充外部客户ROI
- 优化伴随航线/机队/运营变革，不能把全部差值作FDE单一因果

### 来源
1. [客户官方FDE参与](https://s202.q4cdn.com/166167538/files/doc_presentations/2026/05/SurfOS-Go-To-Market.pdf)
2. [客户原始成效新闻稿；web直接打开失败，通过署名syndication核读](https://www.businesswire.com/news/home/20261007789149/en/)
3. [Surf Air Mobility Inc. via Business Wire完整发布稿](https://markets.financialcontent.com/stocks/article/bizwire-2026-10-7-surf-air-mobility-provides-airline-operations-business-update-highlighting-surfos-driven-efficiency-and-electric-aviation-priorities-in-hawaii?Language=english%2F1000)
4. [Surf Air官方：主体所在地与SurfOS运营航线](https://www.surfair.com/brands/)

## 81. NFL：NFL IQ 球迷数据问答

国家：美国；项目落地：未披露
行业：职业体育与球迷媒体
国家口径：联盟总部在美国纽约；网页面向球迷，所引项目资料未列逐国上线范围。

概述：球队、选秀、自由球员等数据散落多个界面，球迷需要自己查找拼接。

流程：NFL CIO直接确认 AWS FDE（Forward Deployed Engineer，前线部署工程师）与客户共同开发 NFL IQ 和 Fantasy AI。此处聚焦前者：Amazon Quick聊天代理、嵌入式仪表板与NFL.com集成。

落地程度：规模对公众上线；2026年3月推出。

人工职责：NFL研究分析人员继续建设数据、模型和视图。未公开每个回答是否人工审核及转人工比例。

证据说明：NFL CIO直接确认 AWS FDE（Forward Deployed Engineer，前线部署工程师）与客户共同开发 NFL IQ 和 Fantasy AI。此处聚焦前者：Amazon Quick聊天代理、嵌入式仪表板与NFL.com集成。

可切入环节：从一组公开数据的赛前/选秀问答做起，用固定问题集测事实准确性、延迟和每次有效回答成本。

- 效率与使用规模：NFL负责人称概念到上线约6周。7月8日官方文章披露自3月上线以来16.8万+独立球迷、8.2万+聊天会话、74.4万+事件；指标精确截止日未给出。。口径：客户或供应商自报；详见口径限制

- 成本变化：未公布合同费、云费用、每次会话成本或成本节省。。口径：未披露项目总投入和净节省

### 介入前的问题与基线

- 【公开披露】球迷原需在选秀榜单、球队需求、深度图等分散页面来回查找，难以随比赛/选秀状态追问。 [来源3](https://aws.amazon.com/blogs/media/how-nfl-next-gen-stats-built-the-nfl-iq-ai-assistant-with-amazon-quick/)

### 工程师具体做了什么

- 【公开披露】AWS嵌入团队与NFL共同构建NFL IQ；官方交付材料报告从概念到上线约6周。 [来源1](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers) [来源2](https://aws.amazon.com/blogs/business-intelligence/ai-powered-productivity-comes-to-the-west-coast/)

### 技术方案与数据流程

- 【公开披露】Amazon Quick提供共享分析层，结构化仪表板加聊天代理嵌入NFL.com；逐步接入精选NFL内容和指标定义，测试路由与回答相关性，按选秀状态选择问题。 [来源3](https://aws.amazon.com/blogs/media/how-nfl-next-gen-stats-built-the-nfl-iq-ai-assistant-with-amazon-quick/)

- 【公开披露】团队迭代验证数据和上下文，不是每个用户回答均由人工实时批准；页面未给模型版本、检索参数和自动评测门槛。 [来源3](https://aws.amazon.com/blogs/media/how-nfl-next-gen-stats-built-the-nfl-iq-ai-assistant-with-amazon-quick/)

- 【分析／复现建议】复现建议，非客户已公开实现：应保留统计时间和数据来源，测试不同队名/球员别名及过期信息，避免把历史预测当实时事实。

### 解决程度与业务提升

- 【公开披露】2026年7月8日AWS文章回顾3月上线后的744000+事件、168000+独立用户、82000+聊天。这是当时观察窗，不是2026年10月当前累计值，也不是收入或人工节省。 [来源2](https://aws.amazon.com/blogs/business-intelligence/ai-powered-productivity-comes-to-the-west-coast/)

### 尚未公开的信息

- 【未披露】用户满意度、回答准确率、延迟、每问费用、实施费及相对旧体验的受控提升未公开。

### 关键技能
- 结构化数据语义层、检索与查询路由、时效刷新、嵌入式分析、消费级峰值容量与观测。

### 风险
- 过期名单、薪资空间口径或模型分数被当作事实；须显示数据时间和不确定性。

### 限制
- 使用量不是准确率、收入或节省；“6周”是本次交付时长，不能在缺少可比基线时算提速百分比。不可把其他NFL伤病模型效果归给此项目。

### 来源
1. [AWS官方：明确工程师共同投产NFL IQ](https://www.aboutamazon.com/news/aws/aws-1-billion-forward-deployed-ai-engineers)
2. [AWS官方：6周上线与使用规模](https://aws.amazon.com/blogs/business-intelligence/ai-powered-productivity-comes-to-the-west-coast/)
3. [AWS官方：NFL IQ技术工作流](https://aws.amazon.com/blogs/media/how-nfl-next-gen-stats-built-the-nfl-iq-ai-assistant-with-amazon-quick/)
4. [National Football League官方：联盟地址](https://support.nfl.com/hc/en-us/articles/35869693160980-League-Address)

## 82. Nubank：核心ETL代码库模块化迁移

国家：巴西；项目落地：未披露
行业：数字银行
国家口径：Nu官方投资者FAQ明确运营总部在巴西圣保罗；集团法律注册地与运营总部不同。本例采用运营总部；代码有br/co/mx模块不等于已证实三个国家部署，实际国家留空。

概述：600万行ETL单体及跨模块依赖使迁移变为大量重复工程工作。

流程：收集人工迁移示例，分出训练与评测集；Devin执行数据类迁移，工程师审查微调后合并。

落地程度：部分业务部门已在数周内验证并完成迁移；未宣称整个银行的全部代码均完成。

人工职责：人工管理项目并批准变更，检查、少量调整后合并PR。

证据说明：部署工程负责人Jia Wu在前线部署工程师（Forward Deployed Engineer）演讲14:11逐项提及Nubank ETL迁移；官方案例第一人称记载定制微调与评测，组合为B。

可切入环节：分析：先挑可自动验证的小模块，保留人工代码审核。

- 工程工时效率：8–12倍。口径：同类数据类迁移任务的人工作业时间，对比提示与审核Devin所需工时；不是全公司生产率。

- 委派范围成本差异：超过20倍。口径：仅比较Devin运行成本与人工时薪完成同任务；未含全部实施维护投入。

- 总投入与净成本：未公开。口径：未披露实施费、订阅费、维护费及扣除全部投入后的净节省。

### 介入前的问题与基线

- 【公开披露】八年ETL单体超过600万行，依赖链可达70层，责任边界不清。原计划由千余工程师在18个月迁移约10万数据类；这是原计划范围，不是已完成量。 [来源1](https://devin.ai/customers/nubank)

### 工程师具体做了什么

- 【公开披露】银行提供人工迁移样例，一部分用于定制微调，其余留作评测。人负责项目管理、审核修改和合并PR。 [来源1](https://devin.ai/customers/nubank)

- 【公开披露】部署工程负责人在演讲中把该ETL迁移列为FDE（Forward Deployed Engineer，前线部署工程师）实践；参与身份是演讲与官方案例组合证据。 [来源2](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)

### 技术方案与数据流程

- 【公开披露】迁移需移动数据类、修正导入及处理跨文件依赖。Devin把按路径判断br/co/mx分支等重复步骤做成脚本；不能把这些国家代码直接当部署地区。 [来源1](https://devin.ai/customers/nubank)

- 【公开披露】在留出评测集上，微调后完成评分约翻倍，单子任务约40→10分钟；评测集规模及绝对完成率未给出。 [来源1](https://devin.ai/customers/nubank)

- 【公开披露】技术背景：Cognition解释其代理用多个模型调用进行规划、执行、评价和工具使用；评测优先用编译器、类型检查、单元测试等确定性检查，再辅以代理评价和人工检查。这不是Nubank已公布的逐项架构。 [来源4](https://cognition.com/blog/evaluating-coding-agents)

- 【分析／复现建议】复现建议，非客户已公开实现：按数据域建立迁移任务清单及依赖图；用同一批历史任务做训练/评测隔离，禁止把验收样例混入训练。

- 【分析／复现建议】复现建议，非客户已公开实现：每个变更保存原始输入、代码差异、自动测试、审核人及回滚点；先验证运行结果和数据语义，再批准合并，不能只看能编译。

- 【分析／复现建议】复现建议，非客户已公开实现：把代理执行时间、工程师审核时间、返工量分开计量，避免用机器运行速度代表人力节约。

### 解决程度与业务提升

- 【公开披露】Data、Collections、Risk等部门数周完成其迁移。相同任务的人力投入效率8—12倍；委派范围运行费对比人工时薪成本差异超过20倍，不含完整总拥有成本。 [来源1](https://devin.ai/customers/nubank)

### 尚未公开的信息

- 【未披露】微调基础模型、参数、样本数、评测任务清单和任务完成绝对分值未披露。

- 【未披露】银行代码访问控制、隔离环境、生产数据权限、审计策略、CI门禁及回滚步骤未披露。

- 【未披露】实际迁移总数、全项目结束日期、实施合同金额及净现金收益未披露；不能把规划18个月直接当实际节省18个月。

### 关键技能
- 分析：迁移任务拆解与评测集
- 分析：跨文件依赖验证

### 风险
- 分析：数据语义或依赖遗漏
- 分析：不能把PR合并当业务正确性证明

### 限制
- 演讲为近似回忆，不使用其50名工程师/三分之一时间取代官方任务口径。
- 前线部署工程师（Forward Deployed Engineer）贡献与Devin产品整体收益不可单独分离。

### 来源
1. [Nubank ETL migration with Devin](https://devin.ai/customers/nubank)
2. [Jia Wu：How Forward Deployed Engineering is done at Cognition](https://ai.engineer/talks/RVxym6mmIns-forward-deployed-engineering-is-done-at-cognition)
3. [Nu investor FAQs](https://nu.com/en/investors/why-invest/faqs/)
4. [Cognition：编码代理评测方法](https://cognition.com/blog/evaluating-coding-agents)

## 83. Superhuman（邮件应用）：Superhuman邮件分类与检索模型生产迁移

国家：美国；项目落地：未披露
行业：电子邮件与办公生产力软件
国家口径：主体国家为美国；来源：Superhuman Labs美国商标程序文件，申请正文列Delaware LLC和San Francisco, CA, UNITED STATES。项目实际落地国家未单独披露，不以总部推断。

概述：邮件应用的分类与检索模型需要低延迟且无需自建GPU运维。

流程：前线部署工程师（Forward Deployed Engineer）与客户机器学习团队联合部署、优化、评测多种嵌入模型；用BEI与性能客户端解决瓶颈，并协助切换生产流量。

落地程度：生产流量已迁移；不是仅基准或试验。

人工职责：Superhuman工程师维护模型与产品，前线部署工程师（Forward Deployed Engineer）协助迁移；用户继续操作邮箱，未披露逐分类人工审核。

证据说明：Baseten官方案例Solutions逐项目说明前线部署工程师（Forward Deployed Engineer）和性能工程师与Superhuman的机器学习工程师及工程管理层一起部署、优化、评测、扩容；Results再次明确前线部署工程师（Forward Deployed Engineer）直接支持生产迁移。

可切入环节：分析建议：先对一个邮件分类模型影子运行，保留旧服务回退后渐进切流。

- 交付周期：1周。口径：Solutions报告该推理优化与迁移项目周期。

- p95延迟：平均降低80%。口径：多种自定义嵌入模型平均值；非所有邮件功能总延迟。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】原服务对最大嵌入模型未达p95<500毫秒目标；需要支持异构自定义模型、全球弹性流量，精简团队不愿自行维护分布式GPU。 [来源1](https://www.baseten.co/resources/customers/superhuman/)

### 工程师具体做了什么

- 【公开披露】FDE（Forward Deployed Engineer，前线部署工程师）和性能工程师与客户机器学习团队共同部署、优化、压测、扩容，一周交付，并协助生产切流。 [来源1](https://www.baseten.co/resources/customers/superhuman/)

### 技术方案与数据流程

- 【公开披露】分类、搜索、检索模型部署到TensorRT-LLM基础的BEI；通过多云容量管理、延迟感知路由和双活支持扩展，同时用Performance Client减少客户端瓶颈。 [来源1](https://www.baseten.co/resources/customers/superhuman/)

- 【公开披露】背景机制：Performance Client用Rust、PyO3释放网络调用期间的GIL，用Tokio调度并发；完成后再组装Python结果。文档的12倍吞吐属于独立极端负载基准，不是Superhuman实测。 [来源3](https://www.baseten.co/blog/your-client-code-matters-10x-higher-embedding-throughput-with-python-and-rust/)

- 【公开披露】BEI面向嵌入、重排、分类模型，支持自定义/微调模型及弹性扩展。通用产品页的2倍吞吐和10%延迟优化不能替代该客户指标。 [来源4](https://www.baseten.co/blog/introducing-baseten-embeddings-inference-bei/)

- 【分析／复现建议】复现建议，非客户已公开实现：数据流按邮件输入→预处理→分类/嵌入服务→结果回应用拆开计时；检索索引和数据库选型仍须另外确认，不补写未披露组件。

- 【分析／复现建议】复现建议，非客户已公开实现：同一输入集同时测服务端和客户端耗时、p50/p95/p99、峰值并发及质量；先影子运行，再切流并保留旧端点回退。

### 解决程度与业务提升

- 【公开披露】数十种自定义嵌入模型的p95平均下降80%；页首列100毫秒响应与20+模型。多个工程师可转向产品工作，具体人数和工时未披露。 [来源1](https://www.baseten.co/resources/customers/superhuman/)

- 【分析／复现建议】复现建议，非客户已公开实现：公司收益可表述为响应更快、减少自建基础设施负担；用户每周节省4小时是整个邮件产品的宣传，不能归因于这次迁移。

### 尚未公开的信息

- 【未披露】模型名称、输入清洗、索引结构、数据保留与邮件权限过滤未披露。

- 【未披露】切流比例、回滚机制、压测样本、分类准确率变化和p95观察期未披露。

- 【未披露】合同、GPU账单、实施费与净节省未披露；不能从80%延迟降幅推出80%成本下降。

### 关键技能
- 分析：异构嵌入模型部署
- 分析：客户端瓶颈诊断
- 分析：低风险生产流量切换

### 风险
- 分析：邮件内容隐私
- 分析：模型迁移质量回退
- 分析：尾延迟和平均值混用

### 限制
- 4小时每周用户节省是Superhuman产品整体说法，不归因为本次模型迁移。
- 客户故事未标发布日期；仅记录核验前已公开。

### 来源
1. [Superhuman achieves 80% faster embedding model inference with Baseten](https://www.baseten.co/resources/customers/superhuman/)
2. [Superhuman Labs美国商标程序文件](https://ttabvue.uspto.gov/ttabvue/ttabvue-98880288-EXT-3.pdf)
3. [Baseten Performance Client技术原理](https://www.baseten.co/blog/your-client-code-matters-10x-higher-embedding-throughput-with-python-and-rust/)
4. [Baseten Embeddings Inference技术背景](https://www.baseten.co/blog/introducing-baseten-embeddings-inference-bei/)

## 84. Zed Industries：Zed代码编辑预测模型优化与生产迁移

国家：美国；项目落地：美国、欧盟
行业：软件开发工具与代码编辑器
国家口径：主体国家美国来自Zed官方条款16.12的公司地址；实际部署地区美国、欧盟来自Baseten案例Highlighted features的Global deployment (USA-EU)，欧盟不拆为未披露成员国。

概述：Zed编辑预测功能需要低尾延迟和可随用户增长扩容的模型推理。

流程：前线部署工程师（Forward Deployed Engineer）与性能团队测试多种优化，以TensorRT-LLM、缓存、推测解码和跨区域路由优化Zeta代码补全，并迁移生产流量。

落地程度：全部流量已迁移；有上线后的继续优化。

人工职责：开发者按Tab接受建议并审阅代码；双方工程师测试和调参。

证据说明：客户故事Solutions直接称把Zed与前线部署及性能工程师配对，详细描述数日内测试75多种优化和上线配置；Results确认生产流量迁移。

可切入环节：分析建议：对固定仓库测试集和真实影子请求评测，逐步切流并保持用户确认。

- p90延迟：降低45%。口径：案例Results给定与原推理服务比较，测量窗口未公开。

- 吞吐量：提高至3.6倍。口径：供应商报告；未公开标准化负载。

- 生产流量切换：1天以内。口径：充分测试后的迁移时长，不是全部研发周期。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】临近发布一周，旧服务未达p90<500毫秒、p50<200毫秒；只有单区域、容量承诺受限，优化过程黑盒且工程支持不足。 [来源1](https://www.baseten.co/resources/customers/zed-industries-serves-2x-faster-code-completions-with-baseten/)

### 工程师具体做了什么

- 【公开披露】FDE（Forward Deployed Engineer，前线部署工程师）与性能团队数日试验75余种优化，联合调整推测解码和扩容参数。 [来源1](https://www.baseten.co/resources/customers/zed-industries-serves-2x-faster-code-completions-with-baseten/)

### 技术方案与数据流程

- 【公开披露】Zeta编辑预测由TensorRT-LLM运行，结合KV缓存、定制推测解码、Lookahead和地理路由；美国与欧盟部署。开发者按Tab接受建议。兼容API经测试后一日内全量切换，官方称无需改代码。 [来源1](https://www.baseten.co/resources/customers/zed-industries-serves-2x-faster-code-completions-with-baseten/)

- 【公开披露】技术背景：Lookahead并行产生候选n-gram再验证，不要求另一个草稿模型。窗口W、n-gram长度N、验证集合G需按模型、硬件、批量和序列长度调参。NVIDIA的Qwen基准并非Zed实测参数。 [来源3](https://developer.nvidia.com/blog/optimizing-qwen2-5-coder-throughput-with-nvidia-tensorrt-llm-lookahead-decoding/)

- 【分析／复现建议】复现建议，非客户已公开实现：工程上应先记录原服务延迟分布，固定输入上下文、模型和生成长度，逐项改变缓存/解码参数；吞吐改善必须同时满足单请求尾延迟。

- 【分析／复现建议】复现建议，非客户已公开实现：代码建议经用户确认只是产品交互，不能替代对私有代码泄露、错误建议和危险修改的测试。上线验收应包含超时降级、地域路由和回滚。

### 解决程度与业务提升

- 【公开披露】p90下降45%，吞吐3.6倍；供应商称上线后继续优化，编辑预测超过原服务两倍快。100%在线率未给观察期，不视为永久保证。 [来源1](https://www.baseten.co/resources/customers/zed-industries-serves-2x-faster-code-completions-with-baseten/)

- 【分析／复现建议】复现建议，非客户已公开实现：商业价值是支持按期发布、跨区域低延迟和工程透明度；没有收入、用户留存或净成本的可归因数字。

### 尚未公开的信息

- 【未披露】75余项实验明细、每项增益、最终W/N/G、GPU及副本数量未披露。

- 【未披露】输入上下文范围、日志与代码保留、访问控制、质量测试集及准确率未披露。

- 【未披露】成本账单、合同费用、实际发布日和可用性测量窗口未披露。

### 关键技能
- 分析：推测解码和缓存优化
- 分析：代码补全质量评估
- 分析：多区域容量与迁移回退

### 风险
- 分析：建议代码缺陷
- 分析：私有代码处理边界
- 分析：延迟改善与吞吐压力取舍

### 限制
- 美国/欧盟为案例Highlighted features明确部署地区；欧盟未细分国家。
- 100%可用性未给观察期，故未作为主要量化结果。

### 来源
1. [How Zed is reimagining the code editor from the ground up](https://www.baseten.co/resources/customers/zed-industries-serves-2x-faster-code-completions-with-baseten/)
2. [Zed官方服务条款](https://zed.dev/terms)
3. [NVIDIA：Lookahead decoding技术详解](https://developer.nvidia.com/blog/optimizing-qwen2-5-coder-throughput-with-nvidia-tensorrt-llm-lookahead-decoding/)

## 85. Writer：Writer医疗与金融专用Palmyra模型部署

国家：美国；项目落地：未披露
行业：企业生成式AI软件与行业语言模型
国家口径：主体国家为美国；来源：Writer官方公司介绍，Offices明确San Francisco (HQ)。项目实际落地国家未单独披露，不以总部推断。

概述：Writer要把自研行业模型以可控延迟和单位成本提供给企业。

流程：前线部署工程师（Forward Deployed Engineer）和性能团队与Writer共同确定推理取舍，使用TensorRT-LLM为Palmyra-Med-70B和Palmyra-Fin-70B构建专用引擎及动态批处理。

落地程度：已部署安全私有推理服务；结果段基准在新模型发布前完成。

人工职责：Writer负责模型与领域应用；双方工程师评测性能，不代表供应商替代医疗或金融专业判断。

证据说明：客户故事Solution明确Writer与Baseten专门的性能团队及前线部署工程师共同工作，随后说明为两款70B行业模型建立推理引擎与部署；有逐项目岗位证据。

可切入环节：分析建议：用固定领域问题和真实负载同时评测输出质量、首token延迟与每请求成本。

- 吞吐量：提高60%。口径：FP16、4张NVIDIA A100的公开基准；不是所有生产负载。

- 首token时间：降低23%。口径：与同组基准一致；未披露完整样本。

- 每百万token成本：降低35%。口径：同组基准下的单位推理成本，非企业总成本。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】Writer擅长训练领域模型，但两款70B模型的多GPU推理优化会分散研发精力；需要兼顾延迟、吞吐、成本和私有安全部署。 [来源1](https://www.baseten.co/resources/customers/writer/)

### 工程师具体做了什么

- 【公开披露】FDE（Forward Deployed Engineer，前线部署工程师）和性能团队与Writer确认真实负载和性能取舍，为Palmyra-Med-70B、Palmyra-Fin-70B分别构建引擎。 [来源1](https://www.baseten.co/resources/customers/writer/)

### 技术方案与数据流程

- 【公开披露】用TensorRT-LLM把模型编译为按序列形状和批大小优化的CUDA引擎，支持in-flight batching；在模型发布前完成部署与性能基准。 [来源1](https://www.baseten.co/resources/customers/writer/)

- 【公开披露】背景机制：TensorRT优化发生在训练后、推理前；引擎优化依赖GPU、精度、批大小、输入输出形状。此文为通用解释，并非Writer的完整部署配置。 [来源3](https://www.baseten.co/blog/high-performance-ml-inference-with-nvidia-tensorrt/)

- 【分析／复现建议】复现建议，非客户已公开实现：数据流可按权重→编译引擎→推理端点→应用调用验证；不要把Writer平台的知识图谱、guardrails直接当作本次部署工程师交付的范围。

- 【分析／复现建议】复现建议，非客户已公开实现：冻结验证集并对齐硬件、精度、并发和token长度，测首token/输出速率/单位费用，也检查领域答案质量是否退化。

- 【分析／复现建议】复现建议，非客户已公开实现：医疗或金融场景还需用途分级和专家复核；模型通过考试或某基准不能证明真实医疗/投资决策安全。

### 解决程度与业务提升

- 【公开披露】四张A100、FP16基准：吞吐提高60%、首token时间降低23%、每百万token费用下降35%。H100和推测解码是文末探索方向，不是本期已交付。 [来源1](https://www.baseten.co/resources/customers/writer/)

- 【分析／复现建议】复现建议，非客户已公开实现：可支持的收益是模型服务提速、单位运行费用改善、团队聚焦模型研发；不能据此声称客户诊疗或投资收益提高。

### 尚未公开的信息

- 【未披露】原基准框架、绝对每token费用、batch、序列长度、并发及测量窗口未完整披露。

- 【未披露】私有部署云和地区、权限/密钥管理、审计、容灾及应用级人工审批未披露。

- 【未披露】生产规模、准确率回归、实施费、全部运维与净ROI未披露。

### 关键技能
- 分析：TensorRT-LLM引擎调优
- 分析：批处理和序列形状分析
- 分析：合规边界与性能回归测试

### 风险
- 分析：量化或优化影响领域质量
- 分析：基准与真实负载差异
- 分析：敏感行业信息权限

### 限制
- 两款模型归同一推理平台交付，不拆成两个案例。
- 基准提速不能解释为医疗或金融业务准确率提升。

### 来源
1. [How Writer helps businesses transform with AI](https://www.baseten.co/resources/customers/writer/)
2. [Writer官方公司介绍](https://writer.com/company/about/)
3. [Baseten：TensorRT生产部署原理](https://www.baseten.co/blog/high-performance-ml-inference-with-nvidia-tensorrt/)

## 86. Praktika.ai：Praktika语言学习实时语音转写

国家：美国；项目落地：未披露
行业：在线语言教育与AI口语辅导
国家口径：本例主体采用Praktika.ai Company的注册国家美国：英国Companies House控制主体登记明确为美国特拉华公司，不能因其英国子公司推断项目在英国。案例只称全球用户，实际部署国家未披露。

概述：AI口语教师的语音转文字等待影响会话流畅度。

流程：前线部署工程师（Forward Deployed Engineer）与性能工程师针对Whisper转写优化执行器、动态批处理和自动扩容；验证后迁移流量并持续迭代模型。

落地程度：已迁移生产流量，服务全球语言学习用户；国家明细未披露。

人工职责：学习者与AI对话；客户团队负责教学体验与模型质量，未披露逐段教师复核。

证据说明：Baseten客户故事Solutions明确前线部署工程师与Praktika共同优化转写负载，并说明继续并肩迭代；Results验证后切换生产流量，具备项目级岗位与持续部署动作。

可切入环节：分析建议：从成人已授权语音练习评测开始，分别测各口音准确率和p50/p99响应。

- 转写p50延迟：低于300毫秒。口径：Results口径；旧服务正文给1000–1500毫秒，但未明示同分位数，故不算百分比。

- 转写成本：节省50%。口径：Results针对优化Whisper负载；无绝对金额及完整总成本。

- 成本变化：未公开。口径：未找到项目总拥有成本、服务合同费用及净现金节省；不能由效率百分比推算。

### 介入前的问题与基线

- 【公开披露】旧语音转写耗时约1000—1500毫秒，达不到300毫秒目标；全球增长要求弹性算力，旧供应商缺少持续优化支持。 [来源1](https://www.baseten.co/resources/customers/praktika/)

### 工程师具体做了什么

- 【公开披露】FDE（Forward Deployed Engineer，前线部署工程师）与性能工程团队理解语音负载、优化Whisper执行及扩容，并持续协作迭代。 [来源1](https://www.baseten.co/resources/customers/praktika/)

### 技术方案与数据流程

- 【公开披露】使用TensorRT-LLM C++ executor和in-flight batching，客户可调整自动扩容与运行时。验证Whisper性能后通过OpenAI兼容API迁移流量；更快执行减少所需副本。 [来源1](https://www.baseten.co/resources/customers/praktika/)

- 【公开披露】技术背景：TensorRT-LLM支持包括Whisper在内的多种模型；编译优化要匹配硬件与形状，动态批处理在吞吐与等待时间之间取舍。这不是客户完整配置。 [来源3](https://www.baseten.co/blog/high-performance-ml-inference-with-nvidia-tensorrt/)

- 【分析／复现建议】复现建议，非客户已公开实现：拆分录音上传、排队、转写、对话生成和语音播放延迟；300毫秒指标只属于转写，不能称为整轮对话端到端延迟。

- 【分析／复现建议】复现建议，非客户已公开实现：用不同语种、口音、背景噪声和语速建立固定音频集，测字词错误率与p50/p99。性能测试与真实学习效果测试分开。

- 【分析／复现建议】复现建议，非客户已公开实现：产品应明确录音同意、保存期限、撤回删除及未成年人保护；本案没有公布逐段教师审核，不可声称已有。

### 解决程度与业务提升

- 【公开披露】转写p50低于300毫秒，转写成本节省50%。旧1000—1500毫秒未注明同分位数，故不算精确降幅；没有证据证明学习成绩或续费改善。 [来源1](https://www.baseten.co/resources/customers/praktika/)

### 尚未公开的信息

- 【未披露】Whisper具体版本、语音切片、VAD、采样率、流式协议及精度未披露。

- 【未披露】GPU、batch、扩容阈值、副本数量、具体部署地区、错误率和评测样本未披露。

- 【未披露】费用绝对值、数据保留、教育安全措施、灰度回滚和净收益未披露。

### 关键技能
- 分析：实时语音转写
- 分析：口音和语言质量评测
- 分析：批处理与弹性扩容

### 风险
- 分析：口音识别偏差
- 分析：用户语音隐私
- 分析：把技术延迟误当学习效果

### 限制
- 九种教学语言不等于九个部署国家。
- 成本降幅是转写工作负载，不能等同公司利润或所有AI成本。

### 来源
1. [Praktika delivers ultra-low-latency transcription for global language education with Baseten](https://www.baseten.co/resources/customers/praktika/)
2. [英国Companies House对Praktika.ai Company的主体登记](https://find-and-update.company-information.service.gov.uk/company/16332920/persons-with-significant-control)
3. [Baseten：TensorRT生产部署原理](https://www.baseten.co/blog/high-performance-ml-inference-with-nvidia-tensorrt/)

## 87. Tampa General Hospital：AI医疗利用审核的成本优化

国家：美国；项目落地：美国
行业：医疗服务
国家口径：医院主体与本流程所在地为美国佛罗里达州坦帕。Tampa General官方医院介绍确认佛罗里达业务，官方项目视频指向该院审核流程；未据此扩展至其他医院或国家。

概述：已上线的AI利用审核流程需要在质量不退步的前提下减少模型调用与成本。

流程：AIP Evolve优化AI生成的utilization review（医疗利用审核）；筛选模型、改写prompt、以确定性代码替换部分GPT调用。

落地程度：已规模部署的医疗利用审核辅助流程；官方视频称护士每天与AI共同处理审核。演示界面经过示意处理。

人工职责：护士查看AI提出的利用审核，保留检查、修改、接受并发送步骤；最终医疗决策不由案例中的模型独立承担。

证据说明：Palantir官方DevCon页面及官方LinkedIn视频明确列出前线部署工程师 Colton Rusch。医院专家讲述规模部署后的成本优化；不是尚未发生的活动预告。

可切入环节：先对已有非诊疗文书辅助流程做离线成本优化，质量达标后灰度；不接管临床决策。

- AI工作流成本：降低近70%。口径：医院专家在官方视频称规模部署后的相关AI审核工作流成本下降近70%；绝对金额、基期和样本量未公开。演示中单个criteria-matching agent换模型下降68%，是另一个局部口径，不能当同一分母。不是全院成本下降。

- GPT调用：减少84%。口径：同一优化流程的调用量，不等于人力减少84%。

- 专家偏好：90%情况下偏好优化版。口径：评测样本量、盲测方式未公开；不是临床准确率90%。

- 总投入与净节省：未公开。口径：实施、订阅、维护和绝对美元金额未披露。

### 介入前的问题与基线

- 【公开披露】原有AI利用审核已规模使用，模型费用随部署扩大成为负担。目标是降低这项工作流费用，同时保住临床叙述与证据质量；不是从零替代全院人工。 [来源1](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)

- 【未披露】缺少优化前每份审核的美元成本、调用次数、耗时分布，以及人工审核时长，无法重建绝对基线。

### 工程师具体做了什么

- 【公开披露】官方明确Colton Rusch为FDE（Forward Deployed Engineer，前线部署工程师）；他与医院专家David Zihr共同展示成本优化。工程师展示系统依赖、寻找高成本节点及验证替换效果，医院提供质量约束。 [来源1](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)

### 技术方案与数据流程

- 【公开披露】患者病历与审核指南进入审核流程；Ontology承载人和AI动作及分支关系，混合确定性逻辑与agent。审核稿呈现在护士工作台，与病历对照，经护士修改、接受并发送。 [来源1](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)

- 【公开披露】AIP Evolve分析数据流和模型调用位置。演示中的criteria-matching agent将两处Claude Sonnet替换为GPT-5 mini：该局部成本下降68%，延迟有所增加。不能说整套医院系统统一换成该模型。 [来源1](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)

- 【公开披露】官方项目摘要还披露跨供应商模型筛选、提示修改，以及用确定性代码代替部分模型调用。 [来源2](https://www.palantir.com/devcon/)

- 【公开披露】优化比较要守住临床叙述和证据选择；护士仍复核。公开演示是示意界面，并非公开真实患者资料。 [来源1](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)

- 【公开披露】90%偏好不是90%临床准确率；专家人数、样本量、抽样方式、盲测和失败阈值未披露。 [来源2](https://www.palantir.com/devcon/)

- 【分析／复现建议】以下是复现建议，不是医院已公开架构：先画审核状态机，把输入、输出、人工批准及下游副作用列清楚；记录每节点费用与延迟。

- 【分析／复现建议】建立去标识化测试集，覆盖缺失证据、矛盾病历及边界条件；按医生认可的错误严重度评分。先验证低风险确定性规则，再比较模型替换。

- 【分析／复现建议】以“单份合格审核总成本”验收，并同时监控人工修改量、严重遗漏和P95延迟；达不到质量阈值时回滚。

### 解决程度与业务提升

- 【公开披露】该AI审核工作流成本下降近70%；GPT调用减少84%；医院专家90%的比较中偏好优化输出。三项分别是费用、调用量、专家偏好，不能互相替代。 [来源2](https://www.palantir.com/devcon/)

- 【分析／复现建议】可支持的商业结论是：已有生产流程的模型运行费用下降，同时保留专业人员审核。不能据此推出住院时间缩短、全院利润提升或减少了多少护士。

- 【分析／复现建议】总订阅、实施、维护费用，优化前后绝对账单及净现金节省未公开。68%局部替换与近70%总体工作流不是可相加的两个收益。

### 尚未公开的信息

- 【未披露】EHR产品及具体接口、数据表、消息队列、提示全文：未公开，不能据通用技术推定。

- 【未披露】每个节点模型版本、上下文大小、token账单和缓存策略：未公开，不能据通用技术推定。

- 【未披露】访问控制、患者数据脱敏、保留期限、部署云及地区：未公开，不能据通用技术推定。

- 【未披露】生产变更审批、灰度回滚、模型失效及应急恢复细节：未公开，不能据通用技术推定。

- 【未披露】端到端临床安全评价和独立审计：未公开，不能据通用技术推定。

### 关键技能
- 工作流轨迹与成本拆解
- 模型选择及提示优化
- 以确定性代码替代不必要调用
- 专家评测与上线回归

### 风险
- 医疗审核具有高后果；专家偏好不能代替安全性或临床效果验证
- 降低模型费用可能增加延迟；优化需同时守住证据完整性、质量和人工审核要求。

### 限制
- 仅AI工作流成本，不是全院成本降低70%
- 临床结果来自另一期合作，不应全部归因于GenAI或单个FDE
- 没有独立审计或随机对照

### 来源
1. [官方视频：明确工程师身份、实际使用、护士复核及成本变化](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)
2. [FDE身份、生产阶段、成本与专家偏好](https://www.palantir.com/devcon/)
3. [2026-10-17直接open读取全文；官方公司帖+视频转录，FDE身份/每天生产/护士保留步骤/成本近70%及局部68%演示](https://www.linkedin.com/posts/palantir-technologies_at-devcon6-see-how-dr-david-zihr-medical-activity-7485030356522336256-1oOV)
4. [官方公司2026-07-20成果帖；原站403，日期与正文通过2026-07-21 Palantir Bullets嵌入读取](https://x.com/palantirtech/status/2079263914139758785)
5. [官方Q2 2026报告第11页用过去时回顾DevCon6，证明截至2026-10-17前已发生；正文索引可读，直接open超大小限](https://investors.palantir.com/files/Palantir%20-%20Q2%202026%20Business%20Update.pdf)
6. [Tampa General官方：医院所在地与业务](https://www.tgh.org/about-tgh)

## 88. Morgan Stanley：财富顾问知识检索助手及持续评测

国家：美国；项目落地：未披露
行业：财富管理与投资咨询
国家口径：总部国家来自Morgan Stanley官方美国办公室页，明确美国及纽约世界总部；项目来源未逐项列落地国家，不按总部推断。

概述：财富顾问难以快速检索研究知识，同时需要可靠、合规的回答。

流程：内部助手检索受控文档；顾问和提示工程师评分，双方迭代检索方法，以每日回归集监控质量。

落地程度：生产使用；OpenAI报告超过98%的财富管理顾问团队使用。访谈回顾技术搭建后仍需数月试点与信任建设，不将技术完成等同正式上线。

人工职责：顾问判断答案是否适用于客户；专家参与准确性评分与评测门槛。

证据说明：前线部署工程师（Forward Deployed Engineer）负责人Colin Jarvis接受Altimeter访谈，主持人原始发布将Morgan Stanley列为前线部署工程师（Forward Deployed Engineer）实战；OpenAI项目案例补足实际采用与评测工作流。属于参与者访谈与官方项目的B组合。

可切入环节：先选受控研究库，设置专业人员评分和明确拒答条件。

- 采用率：超过98%。口径：官方顾问团队口径，非所有员工或模型准确率。

- 文档覆盖：100,000份。口径：官方称可回答该语料问题；不代表每份文档都被人工逐条验证。

- 成本：未公开。口径：无完整投入和净收益。

### 介入前的问题与基线

- 【公开披露】顾问需要查找和总结大量内部研究资料；项目优先解决检索耗时、重复摘要及回答可靠性。 [来源2](https://openai.com/index/morgan-stanley/)

- 【未披露】原先每次搜索平均耗时、失败率和人员成本未披露，不能自行编造“从几小时降为几秒”。

### 工程师具体做了什么

- 【公开披露】OpenAI部署工程负责人Colin Jarvis访谈将此列为FDE（Forward Deployed Engineer，前线部署工程师）实践：技术链路约6—8周打通，随后约6个月试点、评测和迭代建立顾问信任。这是负责人回顾，非原团队每位成员职称证明。 [来源1](https://tailwinds.substack.com/p/metabolize-pain-excrete-product-the)

- 【公开披露】双方根据顾问及提示工程师的准确性、连贯性评分优化提示和检索；每天用样本问题做回归测试。 [来源2](https://openai.com/index/morgan-stanley/)

### 技术方案与数据流程

- 【公开披露】已披露主链路：顾问提问→内部知识检索→GPT-4组织回答→顾问使用。语料覆盖100,000份文档。官方称零数据保留解决专有信息顾虑。 [来源2](https://openai.com/index/morgan-stanley/)

- 【未披露】具体向量数据库、embedding型号、分块长度、重排器、top-k、权限过滤实现和基础设施未公开。不能因为这是检索增强应用，就补写Pinecone、LangChain或某云服务。

- 【分析／复现建议】专家评测驱动迭代和日常回归，不意味着零错误。高采用率也是使用指标，不是准确率或投资表现。

- 【公开披露】补充：2024-06-26推出的Debrief是另一条流程，客户同意后形成会议笔记与行动项，写入Salesforce，并由顾问编辑发送邮件。官方引述一名顾问每次会议约节省半小时，不能当全公司平均数，也不能归入Assistant的节省。 [来源4](https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch)

- 【分析／复现建议】以下为可复现建议，非该公司架构：先选一套权限清楚的知识库，给每条来源保留版本和可见范围；做检索与回答两级评价，不只问答案“像不像对的”。

- 【分析／复现建议】让领域专家标注可回答、应拒答和证据不足的真实问题；检索失败和生成错误分开定位。每次换模型、文档或提示都跑回归。

- 【分析／复现建议】商业验收同时看任务完成率、人工核验时长和活跃使用；采用率不能替代质量。涉及投资行动时保留专业人员最终判断。

### 解决程度与业务提升

- 【公开披露】官方披露顾问团队采用超过98%，文档访问由20%升至80%；后者未给完整分母定义和观察期，不等于检索准确率提高到80%。 [来源2](https://openai.com/index/morgan-stanley/)

- 【公开披露】访谈摘要还报研究报告使用量约3倍，与20%→80%文档访问是不同口径，不应合并。 [来源1](https://tailwinds.substack.com/p/metabolize-pain-excrete-product-the)

- 【公开披露】公司2024-06-26公告确认Assistant于2023年9月全面推出，当时顾问团队采用率98%。 [来源4](https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch)

- 【分析／复现建议】改善可以描述为知识更容易被顾问使用；客户资产增长、投顾收益、营收增量及成本净节省没有该项目可归因数据。

### 尚未公开的信息

- 【未披露】检索的精确率、召回率、严重幻觉率和拒答阈值：未公开，不能据通用技术推定。

- 【未披露】原项目工程师人数、驻场方式、合同费用：未公开，不能据通用技术推定。

- 【未披露】内容权限与客户可见边界的具体实现：未公开，不能据通用技术推定。

- 【未披露】更新频率、延迟SLA、部署地区及运维成本：未公开，不能据通用技术推定。

- 【未披露】Assistant单独的工时节省、净收益、投资回报率：未公开，不能据通用技术推定。

### 关键技能
- 检索增强生成
- 领域专家评测
- 回归测试
- 权限和数据留存设计

### 风险
- 误导性金融回答
- 知识更新和检索权限错误

### 限制
- 前线部署工程师（Forward Deployed Engineer）证据是负责人回顾，不声称2023年原项目成员当时均持该职称。
- 不把Debrief另拆为一个已证实前线部署工程师（Forward Deployed Engineer）项目。
- 采用率为公司报告，非独立审计。

### 来源
1. [访谈主持人的原始发布：Colin Jarvis FDE实战](https://tailwinds.substack.com/p/metabolize-pain-excrete-product-the)
2. [OpenAI官方Morgan Stanley案例](https://openai.com/index/morgan-stanley/)
3. [Morgan Stanley官方全球总部](https://www.morganstanley.com/about-us/global-offices/americas/united-states)
4. [Morgan Stanley官方：Debrief上线及Assistant历史时间线](https://www.morganstanley.com/press-releases/ai-at-morgan-stanley-debrief-launch)

## 89. John Deere：播种季设备推荐与经销商支持

国家：美国；项目落地：未披露
行业：农业装备与农机售后
国家口径：主体总部国家为美国：John Deere官方联系页列全球总部位于伊利诺伊州莫林。推荐系统公开案例没有列出实际上线国家，不能据总部或农机销售市场推断。

概述：农户设备设置、使用状态和天气情境不同，通用提醒缺少操作价值；经销商查手册与诊断耗时。

流程：综合设备遥测、季节与天气、历史使用情况，在售前/设备设置/播种季使用中主动向农户及经销商推荐操作；识别停机或 See & Spray 未启用等情形，辅助诊断并生成季末价值报告。

落地程度：官网称已部署播种季 AI 推荐系统；2025-05-06 客户访谈描述已在用的客户成功与经销商辅助流程。未公开覆盖农户总数、地理范围或系统上线日期。

人工职责：领域专家参与真实样本审查与评测；客户成功团队和经销商收到洞察并支持农户。每条推荐是否必须人工批准、异常转人工比例和持续维护人力未公开。

证据说明：DeployCo官网的 FDE（Forward Deployed Engineer，前线部署工程师）案例区明确列John Deere，说明专家样本审查、自定义评测与已部署推荐系统。

可切入环节：先做一型号设备的告警摘要与有来源的排查建议，由经销商确认后发给农户。

- 客户互动：达到6倍。口径：官网自报；互动定义、原基线、样本数、观察期与对照组未公开。这不是农作物产量或人均生产率。

- 成本变化：未公开。口径：合同费、模型成本、总拥有成本及净现金节省均未知。

### 介入前的问题与基线

- 【公开披露】通用设备提醒可能与天气和农时冲突；农户买了设备未必充分使用功能，经销商排故要翻大量手册和维修记录。 [来源2](https://openai.com/index/john-deere-justin-rose/)

- 【未披露】没有披露本推荐系统的原始互动量、服务成本及排故平均时长。高层谈及的支持比例愿景不作已实现基线或结果。

### 工程师具体做了什么

- 【公开披露】OpenAI Deployment Company明确将其作为部署案例：与领域专家审阅数百个真实样例，定制准确性评测，持续迭代后部署播种季推荐。职责有据，但团队人数、每个人负责的代码及驻场时长未公开。 [来源1](https://deploy.co/)

### 技术方案与数据流程

- 【公开披露】已披露数据链路：设备遥测、历史使用和天气情境→识别功能未开启或设备异常→给客户及经销商操作建议；季末形成价值报告。使用OpenAI API，具体模型未披露。 [来源2](https://openai.com/index/john-deere-justin-rose/)

- 【公开披露】示例是See & Spray未启用或回到传统喷洒时，辅助查找喷杆高度、车速、摄像头清洁等原因。建议链路与设备自身视觉喷药算法需分开。 [来源2](https://openai.com/index/john-deere-justin-rose/)

- 【公开披露】已知评测使用真实样例和领域专家；准确率分数、负样本比例、按季节区域分层、拒答标准以及线上回归频率未公开。 [来源1](https://deploy.co/)

- 【未披露】客户成功人员和经销商在流程内，但是否每条建议必须先人工批准、能否自动改机器设置均未披露；不要画成自动控制农机。

- 【分析／复现建议】以下为复现建议，非John Deere实际架构：从一类设备、一类故障开始，把可验证的传感器事实与生成的操作解释分开；先用规则筛选触发事件，再让模型组织有依据的建议。

- 【分析／复现建议】把天气、设备型号和作业状态作为明确上下文；缺数据时不要补猜。测试集按季节、型号、异常状态分层，并保留经销商反馈。

- 【分析／复现建议】验收看建议被采纳后解决了多少故障、平均恢复时间及单客户支持总成本；点击或互动增长不能直接当农户增收。

### 解决程度与业务提升

- 【公开披露】部署官网报告客户互动达到6倍，未给互动定义、基期、样本或对照。只能按供应商自报采用指标记录。 [来源1](https://deploy.co/)

- 【公开披露】最多70%药剂减少来自See & Spray精准喷洒能力，不能把它全归因于本次推荐系统。高层提出1000:1支持比例属于愿景。 [来源2](https://openai.com/index/john-deere-justin-rose/)

- 【分析／复现建议】业务逻辑：帮助用户真正使用购买的功能，可为续费和服务价值提供依据；实际新增续费、利润、减少停机时长尚无本项目数据。

### 尚未公开的信息

- 【未披露】设备数据接入协议、存储和处理系统：未公开，不能据通用技术推定。

- 【未披露】模型版本、提示词、知识检索是否使用向量数据库：未公开，不能据通用技术推定。

- 【未披露】天气数据提供商、时间粒度、缺失和延迟处理：未公开，不能据通用技术推定。

- 【未披露】机器及农户权限映射、数据所有权和保留规则：未公开，不能据通用技术推定。

- 【未披露】推荐触达渠道、人工审批、误报率与故障兜底：未公开，不能据通用技术推定。

- 【未披露】API费、实施费、每农户成本和净收益：未公开，不能据通用技术推定。

### 关键技能
- 设备遥测与天气数据接入
- 农艺/售后知识建模
- 用真实工况建立评测集
- 把建议接回经销商流程

### 风险
- 错误操作建议可能造成设备或农时损失
- 季节性和天气使效果迁移困难；生产逐条复核制度未公开

### 限制
- 化学品用量减少最多 70% 是 2025 客户访谈中 See & Spray 机器视觉精准喷药设备的结果；即使 DeployCo 摘要合并提及，也不能直接归因为 OpenAI 推荐系统。1000:1 相较 10:1 客户支持比例在原文是 vision，不是已实现值。
- 此客户是农业装备企业，案例应用于农业服务；不将其描述为农场运营商。

### 来源
1. [The OpenAI Deployment Company](https://deploy.co/)
2. [AI helps John Deere transform agriculture](https://openai.com/index/john-deere-justin-rose/)
3. [John Deere官方：全球总部地址](https://www.deere.com/en-us/our-company/contact-us)
