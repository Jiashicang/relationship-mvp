from flask import Flask, render_template, request, jsonify
from flask_cors import CORS
import os
import requests
import json
from datetime import datetime, timedetime

app = Flask(__name__)
CORS(app)

# 关系驾驶舱核心提示词
COCKPIT_PROMPT = """
你是一位专业的职场关系战略顾问。请基于用户信息生成《关系驾驶舱报告》。

用户输入：
关系对象：{target_person}
我的角色：{my_role}
当前关系状态：{current_state}
期望目标：{desired_goal}
具体情境：{specific_context}

请按照以下JSON格式输出：
{
  "报告摘要": {
    "核心诊断": "一句话概括关键问题",
    "机会窗口": "最佳行动时机",
    "预期收益": "改善后的价值"
  },
  "三维度分析": {
    "专业维度": {
      "优势": ["1", "2"],
      "补位机会": "具体合作切入点"
    },
    "人际维度": {
      "沟通风格适配": "对方沟通偏好",
      "信任建立路径": "三步走计划"
    }
  },
  "行动计划": [
    {
      "第1天": "立即执行的小行动",
      "目标": "达成什么结果",
      "话术示例": "具体怎么说"
    }
  ]
}
"""

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/analyze', methods=['POST'])
def analyze():
    try:
        data = request.json
        api_key = os.environ.get('RELATIONSHIP_API_KEY')
        
        if not api_key:
            return jsonify({"error": "API密钥未配置"}), 500
            
        # 这里应该调用DeepSeek API，简化版本先返回示例数据
        example_report = {
            "报告摘要": {
                "核心诊断": "当前关系处于工作必要沟通阶段，缺乏深度连接",
                "机会窗口": "下周一项目汇报会后的15分钟",
                "预期收益": "获得关键支持，项目推进效率提升30%"
            },
            "三维度分析": {
                "专业维度": {
                    "优势": ["技术背景扎实", "项目经验丰富"],
                    "补位机会": "协助其完成数据分析部分"
                },
                "人际维度": {
                    "沟通风格适配": "对方偏好数据驱动、简洁明了的沟通",
                    "信任建立路径": "先证明专业能力，再建立私人连接"
                }
            },
            "行动计划": [
                {
                    "第1天": "准备3个关键数据点",
                    "目标": "在偶遇时展示专业性",
                    "话术示例": "张总，我注意到上次会议提到的数据，我做了些分析..."
                }
            ]
        }
        
        return jsonify(example_report)
        
    except Exception as e:
        return jsonify({"error": str(e)}), 500

if __name__ == '__main__':
    port = int(os.environ.get('PORT', 5000))
    app.run(host='0.0.0.0', port=port)
