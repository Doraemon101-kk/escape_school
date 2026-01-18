# Escape School — 我的第一个完整 Python 项目

完成于 2026 年 1 月。
- 实现了场景跳转、模糊输入、失败/成功结局
- 学会了模块化、继承、测试
# 🏫 Escape School —— 文言逃学大冒险

> **一款基于 Python 的命令行文字冒险游戏**  
> 在私塾先生眼皮底下智取庙会！体验古典文言与现代编程的奇妙碰撞。

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)

---

## 🎮 游戏简介

你是一名清朝私塾学生，今日恰逢庙会，却困于课堂。  
先生戒尺在手，同窗噤若寒蝉——但你心向糖葫芦、皮影戏、打陀螺！

通过选择不同行动（假装肚子疼、翻窗、挖花盆……），你将：
- 躲避先生耳目
- 破解后院谜题
- 最终逃出生天，直奔庙会！

> 💬 游戏全程融入《论语》《弟子规》等经典语录，失败时先生还会罚抄古籍哦！

---

## ✨ 核心特性

- **模块化架构**：场景、路由、引擎分离，符合单一职责原则  
- **集中式路由逻辑**：所有跳转规则统一管理，易于维护与扩展  
- **自动化测试**：100% 覆盖核心路由逻辑（pytest）  
- **工程化包结构**：支持 `python -m escape_school` 标准启动方式  
- **沉浸式文言叙事**：原创剧情 + 随机惩罚事件，增强可玩性  

---

## 📂 项目结构

```
escape_school/
├── __init__.py          # 包初始化文件，标识为 Python 包
├── __main__.py          # 项目入口点，支持 python -m escape_school 启动
├── scenes.py            # 所有游戏场景类（SchoolRoom, Courtyard, WallClimb 等）
├── parser.py            # 集中式路由逻辑函数 route_action()
├── engine.py            # 游戏引擎（Engine）与场景映射（Map）
└── tests/
    └── test_parser.py   # 路由逻辑的单元测试（pytest）
```

> 💡 **设计亮点**：  
> - `scenes.py` 仅负责文本输出，不包含任何跳转决策  
> - `parser.py` 是纯函数，无副作用，可独立测试  
> - 完全解耦“输入解析”、“业务逻辑”与“界面展示”

---

## 🚀 快速开始

### 环境要求
- Python 3.8 或更高版本

### 安装与运行
```bash
# 克隆项目
git clone https://github.com/yourname/escape_school.git
cd escape_school

# 启动游戏（推荐方式）
python -m escape_school
```

> ⚠️ **重要**：请勿直接运行 `python scenes.py`，必须使用 `-m` 模式以确保相对导入正常工作。

---

## 🧪 测试

项目包含完整的单元测试，验证所有用户输入路径是否正确跳转：

```bash
# 安装测试依赖（如未安装）
pip install pytest

# 运行测试
python -m pytest tests/ -v
```

✅ 预期成功输出示例：
```
tests/test_parser.py::test_school_room PASSED
tests/test_parser.py::test_courtyard PASSED
tests/test_parser.py::test_wall_climb PASSED
```

---

## 🛠 开发指南

### 如何添加新场景？
1. 在 `scenes.py` 中定义新的 `Scene` 子类  
2. 在 `engine.py` 的 `Map.scenes` 字典中注册该场景  
3. 若需响应用户输入，在 `parser.py` 的 `route_action` 函数中添加跳转规则  
4. 在 `tests/test_parser.py` 中编写对应的测试用例  

### 路由逻辑规范
所有跳转必须通过 `route_action(current_scene: str, user_input: str) -> str` 实现，例如：
```python
if current_scene == "courtyard":
    if user_input == "挖花盆":
        return "temple_fair"
    elif user_input == "翻墙":
        return "wall_climb"
    else:
        return "courtyard"
```

---

## 📜 许可证

本项目采用 MIT License。详情见 [LICENSE](LICENSE) 文件。

---

## 🙏 致谢

- **《笨办法学 Python 3》（Learn Python the Hard Way）**  
  本项目受其“通过构建完整项目学习编程”的理念启发，是 LPTHW 第43章项目的延伸与重构。

## 🤖 AI开发说明

本项目代码初稿由 AI 辅助生成，但所有内容均经过本人逐行阅读、测试与修改。  
我通过此项目深入理解了 Python 包结构、模块化设计、单元测试及命令行交互逻辑。
庙会可以逃，但知识不能逃

- **中华传统文化典籍**  
  游戏中的文言语料参考自《论语》《礼记》《大学》《孟子》《弟子规》等儒家经典，致敬千年智慧。

- **Python 开源生态**  
  感谢 Python 标准库（如 `textwrap`, `sys`, `random`）及 `pytest` 测试框架，让小型项目也能具备工程级质量与可维护性。

---

> **“学而时习之，不亦说乎？” —— 但今天，先去庙会！** 🍡