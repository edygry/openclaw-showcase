<template>
  <div class="app">
    <header class="header">
      <div class="container">
        <h1>🦞 OpenClaw Skills Showcase</h1>
        <p class="subtitle">Discover cool skills, AI industry insights, and open source tools</p>
        <nav class="nav">
          <a href="#skills">Skills</a>
          <a href="#industry">Industry</a>
          <a href="#tools">Tools</a>
          <a href="#hardware">Hardware</a>
        </nav>
      </div>
    </header>

    <main class="container">
      <!-- Featured Skills Section -->
      <section id="skills" class="section">
        <h2>🌟 Featured OpenClaw Skills</h2>
        <p class="section-desc">Community-adopted skills that are proven in real-world usage</p>
        
        <div class="skills-grid">
          <div class="skill-card" v-for="skill in featuredSkills" :key="skill.name">
            <h3>{{ skill.name }}</h3>
            <p class="skill-desc">{{ skill.description }}</p>
            <div class="skill-tags">
              <span v-for="tag in skill.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
            <a :href="skill.url" target="_blank" class="skill-link">View Skill →</a>
          </div>
        </div>
        
        <div class="install-command">
          <code>npx clawhub install {{ selectedSkill }}</code>
          <button @click="copyInstall" class="copy-btn">Copy</button>
        </div>
      </section>

      <!-- AI Industry Commentary -->
      <section id="industry" class="section">
        <h2>📰 AI Industry Commentary</h2>
        <p class="section-desc">How AI advancements affect products like OpenClaw</p>
        
        <div class="articles">
          <div class="article" v-for="article in articles" :key="article.title">
            <h3>{{ article.title }}</h3>
            <p class="article-date">{{ article.date }}</p>
            <p>{{ article.content }}</p>
            <div class="article-tags">
              <span v-for="tag in article.tags" :key="tag" class="tag">{{ tag }}</span>
            </div>
          </div>
        </div>
      </section>

      <!-- State-of-the-Art Tools -->
      <section id="tools" class="section">
        <h2>🛠️ State-of-the-Art Tools</h2>
        <p class="section-desc">New tools shaping the AI landscape</p>
        
        <div class="tools-grid">
          <div class="tool-card" v-for="tool in tools" :key="tool.name">
            <h3>{{ tool.name }}</h3>
            <p class="tool-type">{{ tool.type }}</p>
            <p>{{ tool.description }}</p>
            <div class="tool-comparison">
              <span v-for="feature in tool.features" :key="feature" class="feature">✓ {{ feature }}</span>
            </div>
            <a :href="tool.url" target="_blank" class="tool-link">Learn More →</a>
          </div>
        </div>
      </section>

      <!-- Open Source AI -->
      <section id="opensource" class="section">
        <h2>🌍 Open Source AI</h2>
        <p class="section-desc">Model hosting, community projects, and open source discussions</p>
        
        <div class="oss-grid">
          <div class="oss-card" v-for="project in ossProjects" :key="project.name">
            <h3>{{ project.name }}</h3>
            <p class="oss-type">{{ project.type }}</p>
            <p>{{ project.description }}</p>
            <div class="oss-stats">
              <span>⭐ {{ project.stars }}</span>
              <span>🍴 {{ project.forks }}</span>
            </div>
            <a :href="project.url" target="_blank" class="oss-link">View Project →</a>
          </div>
        </div>
      </section>

      <!-- AI Hardware Tools -->
      <section id="hardware" class="section">
        <h2>💻 AI Hardware Comparison</h2>
        <p class="section-desc">Tools for acquiring AI hardware and optimizing your setup</p>
        
        <div class="hardware-table">
          <table>
            <thead>
              <tr>
                <th>Hardware</th>
                <th>VRAM</th>
                <th>Price</th>
                <th>Best For</th>
              </tr>
            </thead>
            <tbody>
              <tr v-for="hw in hardware" :key="hw.name">
                <td>{{ hw.name }}</td>
                <td>{{ hw.vram }}</td>
                <td>{{ hw.price }}</td>
                <td>{{ hw.bestFor }}</td>
              </tr>
            </tbody>
          </table>
        </div>
        
        <div class="hardware-tools">
          <h3>📊 Available Tools</h3>
          <div class="tool-list">
            <div class="tool-item" v-for="tool in hardwareTools" :key="tool.name">
              <h4>{{ tool.name }}</h4>
              <p>{{ tool.description }}</p>
              <button @click="downloadTool(tool)" class="download-btn">Download</button>
            </div>
          </div>
        </div>
      </section>
    </main>

    <footer class="footer">
      <div class="container">
        <p>Built with Vue 3 + Vite | Deployed on GitHub Pages</p>
        <p>Open source AI tools and community skills showcase</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      selectedSkill: 'memory',
      featuredSkills: [
        {
          name: 'Memory (Obsidian Sync)',
          description: 'Transforms OpenClaw from a session-based tool to a persistent agent with long-term memory',
          tags: ['Memory', 'Productivity', 'Obsidian'],
          url: 'https://clawhub.ai/skills/memory'
        },
        {
          name: 'Morning Briefing',
          description: 'Daily briefing skill that summarizes emails, calendar, and news',
          tags: ['Productivity', 'Automation', 'Email'],
          url: 'https://clawhub.ai/skills/morning-briefing'
        },
        {
          name: 'GitHub Integration',
          description: 'Full GitHub operations - issues, PRs, CI runs, code review',
          tags: ['Developer', 'GitHub', 'CI/CD'],
          url: 'https://clawhub.ai/skills/github'
        },
        {
          name: 'Email Management',
          description: 'CLI to manage emails via IMAP/SMTP with multiple account support',
          tags: ['Email', 'Productivity', 'Automation'],
          url: 'https://clawhub.ai/skills/himalaya'
        },
        {
          name: 'Browser Automation',
          description: 'JavaScript-first browser automation with Playwright integration',
          tags: ['Browser', 'Automation', 'Playwright'],
          url: 'https://clawhub.ai/skills/browser-automation'
        },
        {
          name: 'Task Queue',
          description: 'Asynchronous task management with subagent support and error handling',
          tags: ['Task Management', 'Automation', 'Subagents'],
          url: 'https://github.com/edygry/task-queue'
        }
      ],
      articles: [
        {
          title: 'OpenClaw Skills: From Session Tool to Persistent Agent',
          date: 'April 2026',
          content: 'The Memory skill transforms OpenClaw from a session-based tool to a persistent agent. With long-term memory, OpenClaw can now remember conversations, preferences, and context across sessions.',
          tags: ['Memory', 'Persistence', 'Agent']
        },
        {
          title: 'AI Model Hosting: Running Models Locally vs Cloud',
          date: 'April 2026',
          content: 'With the rise of open source models like Llama 3, Mistral, and Qwen, developers can now run AI models locally. This affects how OpenClaw integrates with different providers and the cost-benefit analysis of local vs cloud hosting.',
          tags: ['Model Hosting', 'Local AI', 'Open Source']
        },
        {
          title: 'The Impact of Opencode on AI Agent Development',
          date: 'April 2026',
          content: 'Opencode represents a new wave of AI coding tools. Its state-of-the-art features are pushing the boundaries of what AI agents can do, influencing how OpenClaw skills are designed and implemented.',
          tags: ['Opencode', 'Coding', 'AI Tools']
        },
        {
          title: 'Security in OpenClaw Skills: What to Watch For',
          date: 'March 2026',
          content: 'With 820+ malicious skills found in ClawHub marketplace, security is paramount. Always review skill code before installing, treat vague docs as red flags, and use the ClawHub CLI for safe installation.',
          tags: ['Security', 'ClawHub', 'Best Practices']
        }
      ],
      tools: [
        {
          name: 'Opencode',
          type: 'AI Coding Tool',
          description: 'State-of-the-art AI coding assistant with advanced code understanding and generation',
          features: ['Advanced code understanding', 'Multi-file editing', 'Terminal integration'],
          url: 'https://opencode.ai'
        },
        {
          name: 'Gemini CLI',
          type: 'AI Agent',
          description: 'Google\'s Gemini CLI for one-shot Q&A, summaries, and generation',
          features: ['Free tier available', 'Google account login', 'Multi-model support'],
          url: 'https://geminicli.com'
        },
        {
          name: 'Qwen Coding Plan',
          type: 'AI Coding Plan',
          description: 'Subscription-based Qwen access with dedicated quota for coding tasks',
          features: ['6,000 requests/5h', '45,000/week', 'Multiple models'],
          url: 'https://qwencloud.com'
        }
      ],
      ossProjects: [
        {
          name: 'Llama 3',
          type: 'Language Model',
          description: 'Meta\'s open source LLM, great for local hosting and fine-tuning',
          stars: '120k',
          forks: '25k',
          url: 'https://github.com/meta-llama/llama3'
        },
        {
          name: 'Mistral 7B',
          type: 'Language Model',
          description: 'Efficient 7B parameter model, perfect for local deployment',
          stars: '45k',
          forks: '8k',
          url: 'https://github.com/mistralai/mistral-src'
        },
        {
          name: 'Ollama',
          type: 'Model Runner',
          description: 'Run LLMs locally with simple CLI, perfect for OpenClaw integration',
          stars: '85k',
          forks: '12k',
          url: 'https://github.com/ollama/ollama'
        },
        {
          name: 'vLLM',
          type: 'Inference Engine',
          description: 'High-throughput serving engine for LLMs, great for production',
          stars: '30k',
          forks: '5k',
          url: 'https://github.com/vllm-project/vllm'
        }
      ],
      hardware: [
        { name: 'RTX 4090', vram: '24GB', price: '$1,600', bestFor: 'Local LLM inference' },
        { name: 'RTX 4080', vram: '16GB', price: '$1,200', bestFor: 'Mid-range AI workloads' },
        { name: 'RTX 3090', vram: '24GB', price: '$800', bestFor: 'Budget 24GB VRAM' },
        { name: 'Mac Studio M2', vram: '192GB', price: '$3,999', bestFor: 'Large model hosting' },
        { name: 'Cloud GPU (Lambda)', vram: '80GB', price: '$1.50/hr', bestFor: 'Training/fine-tuning' }
      ],
      hardwareTools: [
        {
          name: 'VRAM Calculator',
          description: 'Calculate how much VRAM you need for different model sizes and batch sizes'
        },
        {
          name: 'Cost Comparison Spreadsheet',
          description: 'Compare cloud GPU costs vs buying hardware for your AI workload'
        },
        {
          name: 'Model Hosting Guide',
          description: 'Step-by-step guide to hosting models locally with Ollama and vLLM'
        }
      ]
    }
  },
  methods: {
    copyInstall() {
      const text = `npx clawhub install ${this.selectedSkill}`
      navigator.clipboard.writeText(text)
      alert('Copied to clipboard!')
    },
    downloadTool(tool) {
      alert(`Download tool: ${tool.name}\n\nThis would download a CSV/JSON file with detailed comparison data.`)
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  background: #f5f7fa;
  color: #333;
  line-height: 1.6;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.header {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 60px 0;
  text-align: center;
}

.header h1 {
  font-size: 2.5rem;
  margin-bottom: 10px;
}

.subtitle {
  font-size: 1.2rem;
  opacity: 0.9;
  margin-bottom: 20px;
}

.nav {
  display: flex;
  justify-content: center;
  gap: 20px;
  flex-wrap: wrap;
}

.nav a {
  color: white;
  text-decoration: none;
  padding: 8px 16px;
  border: 1px solid rgba(255,255,255,0.3);
  border-radius: 20px;
  transition: all 0.3s;
}

.nav a:hover {
  background: rgba(255,255,255,0.1);
}

.section {
  padding: 60px 0;
  border-bottom: 1px solid #eee;
}

.section:last-child {
  border-bottom: none;
}

.section h2 {
  font-size: 2rem;
  margin-bottom: 10px;
  color: #333;
}

.section-desc {
  color: #666;
  margin-bottom: 30px;
  font-size: 1.1rem;
}

.skills-grid, .tools-grid, .oss-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
  margin-bottom: 30px;
}

.skill-card, .tool-card, .oss-card {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s;
}

.skill-card:hover, .tool-card:hover, .oss-card:hover {
  transform: translateY(-5px);
}

.skill-card h3, .tool-card h3, .oss-card h3 {
  margin-bottom: 10px;
  color: #333;
}

.skill-desc, .tool-card p, .oss-card p {
  color: #666;
  margin-bottom: 10px;
}

.skill-tags, .article-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 5px;
  margin-bottom: 10px;
}

.tag {
  background: #e3f2fd;
  color: #1976d2;
  padding: 3px 8px;
  border-radius: 12px;
  font-size: 0.8rem;
}

.skill-link, .tool-link, .oss-link {
  color: #667eea;
  text-decoration: none;
  font-weight: bold;
}

.skill-link:hover, .tool-link:hover, .oss-link:hover {
  text-decoration: underline;
}

.install-command {
  background: #2d2d2d;
  color: #f8f8f2;
  padding: 15px;
  border-radius: 8px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 500px;
  margin: 0 auto;
}

.copy-btn {
  background: #667eea;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
}

.articles {
  display: grid;
  gap: 20px;
}

.article {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.article h3 {
  margin-bottom: 5px;
}

.article-date {
  color: #999;
  font-size: 0.9rem;
  margin-bottom: 10px;
}

.tool-type, .oss-type {
  color: #667eea;
  font-weight: bold;
  margin-bottom: 5px;
}

.tool-comparison {
  display: grid;
  gap: 5px;
  margin: 10px 0;
}

.feature {
  color: #4caf50;
  font-size: 0.9rem;
}

.hardware-table {
  overflow-x: auto;
  margin-bottom: 30px;
}

table {
  width: 100%;
  background: white;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

th, td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid #eee;
}

th {
  background: #667eea;
  color: white;
}

.hardware-tools {
  margin-top: 30px;
}

.hardware-tools h3 {
  margin-bottom: 20px;
}

.tool-list {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}

.tool-item {
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.tool-item h4 {
  margin-bottom: 10px;
}

.download-btn {
  background: #667eea;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 5px;
  cursor: pointer;
  margin-top: 10px;
}

.footer {
  background: #333;
  color: white;
  padding: 30px 0;
  text-align: center;
}

@media (max-width: 768px) {
  .header h1 {
    font-size: 2rem;
  }
  
  .skills-grid, .tools-grid, .oss-grid {
    grid-template-columns: 1fr;
  }
  
  .nav {
    flex-direction: column;
    align-items: center;
  }
}
</style>
