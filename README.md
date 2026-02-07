# 遁甲归一 (Dunjia GuiYi) - High-Precision Qi Men Dun Jia Engine

[![GitHub Pages](https://img.shields.io/badge/Deploy-GitHub%20Pages-success)](https://weig19364.github.io/dunjia/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Wasm](https://img.shields.io/badge/Core-WebAssembly-purple)](https://webassembly.org/)

**遁甲归一** 是一款基于瑞士星历表（Swiss Ephemeris）算法的高精度奇门遁甲排盘系统。它不仅实现了茅山派传统的转盘与飞盘逻辑，更解决了公元1582年前儒略历与格里历的换算偏差问题，实现了真正的天文级排盘。

> **[在线体验 Live Demo](https://weig19364.github.io/dunjia/)**

---

## ✨ 核心亮点 (Key Features)

### 1. 天文级精度 (Astronomical Precision)
- **瑞士星历内核**: 底层采用编译为 WASM 的 C++ 天文内核 (`AstroKernel`)，计算精度远超传统查表法。
- **真太阳时**: 自动根据经纬度计算真太阳时，定局更精准。
- **节气精确到秒**: 采用牛顿迭代法计算太阳黄经，精准判定节气交接时刻。

### 2. 历史历法自动修正 (Julian/Gregorian Correction)
解决了绝大多数万年历在 1582 年 10 月 15 日之前的计算错误。
- **自动映射**: 对 1582 年前的日期自动进行“儒略历 -> 天文格里历”的偏差修正。
- **案例验证**: 公元 1360 年 5 月 2 日（儒略历），系统能正确修正为 5 月 10 日（天文历），从而得出正确的**癸酉日**（而非错误的乙丑日）及**立夏节气**（而非谷雨）。

### 3. 专业的排盘体系 (Professional Charting)
- **支持盘式**: 
  - 转盘奇门 (Zhuan Pan)
  - 飞盘奇门 (Fei Pan)
- **排盘细节**:
  - 严格遵循茅山派理法。
  - 包含年、月、日、时四柱及空亡。
  - 完整展示九星、八门、八神、天盘干、地盘干。
  - 支持中五宫寄宫处理（阳遁寄艮八，阴遁寄坤二）。

### 4. 历法对比工具
- 提供牛顿法与弦截法的节气/朔日计算对比，供天文算法爱好者研究差异。
- 高精度农历月历表生成。

---

## 🛠️ 技术栈 (Tech Stack)

- **Frontend**: Vanilla JavaScript (ES6 Modules), HTML5, CSS3
- **Computation**: WebAssembly (WASM) for C++ Astro Core
- **Build Tool**: Vite
- **Libraries**: 
  - `SunCalc` (用于日出日落辅助计算)
  - `AstroKernel.js` (自研/移植的高精度天文内核)

---

## 🚀 本地运行 (Development)

如果你想在本地运行或修改代码：

1. **克隆项目**
   ```bash
   git clone [https://github.com/weig19364/dunjia.git](https://github.com/weig19364/dunjia.git)
   cd dunjia
安装依赖

Bash
npm install
启动开发服务器

Bash
npm run dev
访问 http://localhost:5173 即可看到效果。

构建生产版本

Bash
npm run build
📂 项目结构 (File Structure)
Plaintext
dunjia/
├── index.html          # 入口页面
├── app.js              # UI 交互与业务逻辑主入口
├── AstroKernel.js      # 天文内核封装 (WASM 桥接与历法修正)
├── DunJiaKernel.js     # 奇门遁甲排盘算法核心 (转盘/飞盘逻辑)
├── Formula.js          # 基础公式库
├── DunjiaCore.wasm     # C++ 编译的天文计算模块
├── DunjiaCore.js       # WASM 加载器
└── ...
📝 算法验证案例 (Verification)
为了验证算法的准确性，我们在 test_verify.js 中对比了历史极端案例：

输入: 公元 1360年 5月 2日 10:06 (儒略历)

修正处理: 系统自动识别并修正为格里历 1360年 5月 10日。

节气判定: 立夏（而非谷雨）。

日柱结果: 癸酉 (正确)。

传统算法错误结果: 乙丑 (偏差 8 天)。

⚠️ 免责声明 (Disclaimer)
本项目提供的排盘结果仅供学术研究、历法考证及娱乐参考。不应作为任何重大决策的唯一依据。开发者不对因使用本软件而产生的任何后果负责。

📄 开源协议 (License)
MIT License © 2026 Weig19364


### 💡 建议你做的一步操作：

你的项目中提到了 `vite.config.js`，这说明是一个标准的 Node.js 工程。为了让别人能在 GitHub 上一眼看懂你的项目效果，建议你：

1.  **截一张图**：在你的浏览器里打开排盘界面，截取一张排盘成功的图片（最好是那个 1360 年的案例，或者今天的排盘）。
2.  **上传图片**：把图片放到项目根目录（或者新建一个 `screenshots` 文件夹）。
3.  **修改 README**：在 `## ✨ 核心亮点` 这一节下面，或者标题下面，插入图片：
    ```markdown
    ![软件截图](./screenshot.png)
    ```

这个 README 突出了你的**技术壁垒**（WASM、历史历法修正），这会让你的开源项目在众多排盘软件中脱颖而出。
