<<<<<<< HEAD
# gailuopu-analyze-web
盖洛普优势分析
=======
const express = require('express');
const cors = require('cors');

const app = express();
app.use(cors()); // 允许所有前端跨域访问
app.use(express.json()); // 支持 JSON 请求体

// 模拟报告接口
app.post('/api/report', (req, res) => {
  const { name, birthday, strength } = req.body;

  if (!name || !birthday || !strength) {
    return res.status(400).json({ error: '缺少必要字段' });
  }

  // 模拟数据
  const level = 'A（高度匹配）';
  const score = Math.floor(Math.random() * 20) + 80;
  const recommends = ['心理咨询师', '生涯教练', '战略顾问'];
  const avoids = ['流程型行政', '重复操作员'];

  const randomRecommend = recommends[Math.floor(Math.random() * recommends.length)];
  const randomAvoid = avoids[Math.floor(Math.random() * avoids.length)];

  const suggestion = `你具备【${strength}】型优势，结合出生信息 ${birthday}，命理中阳性能量较强，适合探索深度沟通类与策略引导类岗位。建议在未来职业路径中避开过度机械重复的岗位，发挥你的思维与表达力。`;

  res.json({
    name,
    birthday,
    strength,
    level,
    score,
    recommend: randomRecommend,
    avoid: randomAvoid,
    suggestion
  });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`报告分析服务已启动：http://localhost:${PORT}`);
});
>>>>>>> ab26549 (initial commit)
