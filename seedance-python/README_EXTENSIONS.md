# Seedance Python Extensions

Inkos 项目的 Python 自定义扩展——小说转剧本、人物提示词生成等接口。

## 模块说明

### 🎬 小说转剧本 (`extractors/`)
- `novel_extractor.py` — 从 InkOS 生成的小说内容中提取剧本素材（角色、场景、对话、冲突、主题），转换为 Seedance 可用的 UnifiedStory 格式

### 👤 人物提示词 (`agents/character_design.py` + `prompts/`)
- `character_design.py` — 角色视觉形象设计 Agent，生成 Seedance 视频生成提示词和图像提示词
- `prompts/characters_prompts.md` — 人物提示词模板（中文）
- `prompts/characters_prompts_en.md` — 人物提示词模板（英文）
- `prompts/storyboard_chapter01_prompts.md` — 分镜提示词模板

### 🤖 Agent 团队 (`agents/`)
- `director.py` — 导演 Agent，项目规划与统筹
- `screenplay.py` — 编剧 Agent，分镜剧本生成
- `character_design.py` — 美术师 Agent，角色形象设计
- `action_design.py` — 动作设计 Agent
- `prompt_engineer.py` — 提示词工程 Agent
- `llm_client.py` — LLM 客户端封装（OpenAI / Anthropic）
- `seedance_system.py` — 多 Agent 协同系统

### 🎼 编排器 (`orchestrator/`)
- `core.py` — 创作流水线核心编排器
- `schema.py` — UnifiedStory 统一数据模型
- `clients/inkos_client.py` — InkOS API 客户端

### 🔄 转换器 (`converters/`)
- 多语言/风格转换预留接口

## 安装

```bash
cd seedance-python
pip install -e .
```

或手动添加路径：

```python
import sys
sys.path.insert(0, 'seedance-python')
```

## 使用

```python
from orchestrator import CreativeOrchestrator

orchestrator = CreativeOrchestrator()
result = await orchestrator.run_pipeline({
    "inspiration": "一个关于...的故事",
    "mode": "drama",
    "episodes": 5
})
```

详见 `main.py` 中的示例。
