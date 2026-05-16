# YARA 规则库 - 杀毒软件开发资源

## 已下载的规则库

### 1. signature-base (Neo23x0) ⭐ 推荐
**路径**: `signature-base-master/`

由 Florian Roth 维护的高质量YARA规则集合，包含：
- **APT组织规则**: 100+ 条APT组织恶意软件检测规则
- **通用恶意软件**: 病毒、木马、勒索软件等
- **漏洞利用**: 已知CVE漏洞利用检测
- **IoC指标**: 入侵指标（哈希、域名、IP等）

**特点**: 
- 持续更新，社区活跃
- 质量高，误报率低
- 被多家安全厂商采用

**主要目录**:
- `yara/` - YARA规则文件
- `iocs/` - 入侵指标文件
- `misc/` - 其他检测规则

---

### 2. YARA-Rules/rules
**路径**: `rules-master/`

官方YARA规则社区仓库，分类详细：
- `malware/` - 恶意软件规则
- `maldocs/` - 恶意文档规则
- `cve_rules/` - CVE漏洞规则
- `exploit_kits/` - 漏洞利用工具包
- `email/` - 邮件威胁规则
- `packers/` - 加壳/混淆检测
- `capabilities/` - 恶意行为检测
- `crypto/` - 加密货币挖矿
- `antidebug_antivm/` - 反调试/反虚拟机
- `webshells/` - WebShell检测
- `mobile_malware/` - 移动恶意软件

**特点**:
- 分类清晰，易于管理
- 包含索引文件(index.yar)便于批量加载

---

### 3. ReversingLabs YARA Rules
**路径**: `reversinglabs-yara-rules-develop/`

ReversingLabs公司维护的商业级YARA规则：
- 高质量的恶意软件家族识别
- 详细的元数据信息
- 专业的分类和标签

---

## 使用建议

### 规则加载方式

1. **单文件加载**:
```python
import yara
rules = yara.compile(filepath="path/to/rule.yar")
matches = rules.match(data=file_content)
```

2. **批量加载整个目录**:
```python
import yara
rules = yara.compile(filepaths={
    'namespace1': 'path/to/rules1.yar',
    'namespace2': 'path/to/rules2.yar',
})
```

3. **使用索引文件** (推荐用于rules-master):
```python
rules = yara.compile(filepath="rules-master/index.yar")
```

### 性能优化

1. **编译缓存**: 将编译后的规则保存，避免每次重新编译
```python
rules.save('/path/to/compiled_rules')
# 后续加载
rules = yara.load('/path/to/compiled_rules')
```

2. **选择性加载**: 根据扫描场景选择特定规则集
   - 快速扫描: 只加载通用恶意软件规则
   - 深度扫描: 加载全部规则包括APT规则

3. **规则优先级**: 
   - 高置信度规则优先
   - 自定义规则 > 社区规则

### 规则更新

建议定期更新规则库（每周或每月）：
```bash
# 使用git拉取最新规则
cd signature-base-master && git pull
cd ../rules-master && git pull
```

---

## 规则数量统计

当前共包含 **约1620条** YARA规则文件

---

## 参考链接

- [YARA官方文档](https://yara.readthedocs.io/)
- [signature-base GitHub](https://github.com/Neo23x0/signature-base)
- [YARA-Rules GitHub](https://github.com/YARA-Rules/rules)
- [ReversingLabs YARA](https://github.com/reversinglabs/reversinglabs-yara-rules)

---
精选yara直链（以整理成ndb):主：https://pan.vma.cc/pan/down.php/33a11291fdd98a31abc76c8f81bde4a6.ndb
                        备用:https://pan.tenire.com/down.php/33a11291fdd98a31abc76c8f81bde4a6.ndb
                        备用2：https://wwavs.lanzouv.com/iKxZu3pmiesb

*最后更新: 2026-05-03*
