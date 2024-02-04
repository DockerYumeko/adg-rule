<div align="center">
<h1>AdGuard Rule</h1>
  <p>
    一个简易的Java程序，用于合并与更新 AdGuard 过滤规则
  </p>
<!-- Badges -->
<p>
  <a href="https://github.com/LuoXingchen935/adg-rule">
    <img src="https://img.shields.io/github/last-commit/LuoXingchen935/adg-rule?style=flat-square" alt="last update" />
  </a>
  <a href="https://github.com/LuoXingchen935/adg-rule">
    <img src="https://img.shields.io/github/forks/LuoXingchen935/adg-rule?style=flat-square" alt="forks" />
  </a>
  <a href="https://github.com/LuoXingchen935/adg-rule">
    <img src="https://img.shields.io/github/stars/LuoXingchen935/adg-rule?style=flat-square" alt="stars" />
  </a>
  <a href="https://github.com/LuoXingchen935/adg-rule/issues/">
    <img src="https://img.shields.io/github/issues/LuoXingchen935/adg-rule?style=flat-square" alt="open issues" />
  </a>
  <a href="https://github.com/LuoXingchen935/adg-rule">
    <img src="https://img.shields.io/github/license/LuoXingchen935/adg-rule?style=flat-square" alt="license" />
  </a>
</p>

<h4>
    <a href="#a">项目说明</a>
  <span> · </span>
    <a href="#b">规则订阅</a>
  <span> · </span>
    <a href="#c">快速上手</a>
  <span> · </span>
    <a href="#d">问题反馈</a>
  </h4>
</div>

<p align="center">
    <a href="https://github.com/fordes123/ad-filters-subscriber">感谢原作者Fordes123制作的本软件，请对原作者、原项目Follow/Star/Fork（点此前往原作者）</a>

<!---
 <p align="center">
    <a href="/README_en.md">English </a>
    ·
    <a href="https://github.com/fordes123/adg-rule">简体中文</a>
</p>
-->
<br />

<h2 id="a">📔 项目说明</h2>

本项目旨在按需求整合 `AdGuard` 规则。定时从上游订阅获取规则，去除重复和不受支持的规则并进行分类。

<h2 id="b">🎯 规则订阅</h2>

| 名称           | 说明                                                | Github订阅                                                                              | jsDelivr加速订阅                                                                        |
|--------------|---------------------------------------------------|---------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| `all.txt`    | 去重的规则合集，包含以下所有规则，适用于 `AdGuard` 客户端                | [✈️点此查看](https://raw.githubusercontent.com/LuoXingchen935/adg-rule/mine-use/rule/all.txt)      | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/LuoXingchen935/adg-rule/rule/all.txt)   |
| `adgh.txt`   | 针对 `AdGuardHome` 的规则，包含 `hosts.txt` 和`mylist.txt` | [✈️点此查看](https://raw.githubusercontent.com/LuoXingchen935/adg-rule/mine-use/rule/adgh.txt)   | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/LuoXingchen935/adg-rule/rule/adgh.txt)   |
| `hosts.txt`  | `hosts` 规则，~~包含一些访问加速~~                           | [✈️点此查看](https://raw.githubusercontent.com/LuoXingchen935/adg-rule/mine-use/rule/hosts.txt)  | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/LuoXingchen935/adg-rule/rule/hosts.txt)  |
| `mylist.txt` | 自用补充规则，人工更新                                       | [✈️点此查看](https://raw.githubusercontent.com/LuoXingchen935/adg-rule/mine-use/rule/mylist.txt) | [🚀点此查看(延迟)](https://cdn.jsdelivr.net/gh/LuoXingchen935/adg-rule/rule/mylist.txt) |

<br/>
<h2 id="c">🛠️ 快速开始</h2>

#### 示例配置

```yaml
application:
  rule:       
    #远程规则订阅，仅支持http、https
    remote:
      - 'https://example.com/list.txt'
    #本地规则，请将文件移动到项目路径rule目录中
    local: 
      - 'mylist.txt'
  output:
    path: rule   #规则文件输出路径，相对路径默认从 项目目录开始
    files:
      all.txt:    #输出文件名
        - DOMAIN  #域名规则，仅完整域名
        - REGEX   #正则规则，包含正则的域名规则，AdGH支持
        - MODIFY  #修饰规则，添加了一些修饰符号的规则，AdG支持
        - HOSTS   #Hosts规则
```

#### 直接运行

```bash
git clone https://github.com/fordes123/adg-rule.git
cd adg-rule
mvn clean
mvn spring-boot:run
```

#### 使用 Github Action

- fork本项目
- 参照示例配置，修改配置文件: `src/main/resources/application.yml`，注意本地规则文件应放入项目根目录 `rule` 文件夹
- 编辑 `.github/workflows/auto-update.yml` 文件，将 `Commit Changes` 区块下邮箱与用户名修改为自己的（Github邮箱与用户名）
- 提交所有修改并等待 `Github Action` 执行，执行完成后相应规则生成在配置中指定的目录下

<h2 id="d">💬 问题反馈</h2>

- 👉 [issues](https://github.com/LuoXingchen935/adg-rule/issues)
