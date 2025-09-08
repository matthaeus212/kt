# kt

// 📁 design-system/
// 간단하고 효율적인 디자인 토큰 기반 시스템 (Storybook 없이)

/*
Directory Structure:

📁 design-system/
├─ 📁 tokens/             // 디자인 토큰 JSON
│   └─ color.json
├─ 📁 build/              // Style Dictionary 결과물 (CSS, JS)
├─ 📁 src/                // React 컴포넌트
│   └─ Button.jsx
├─ 📄 style-dictionary.config.js
├─ 📄 .gitignore
├─ 📄 package.json
└─ 📄 README.md
*/

// 📄 tokens/color.json
{
  "color": {
    "primary": {
      "value": "#007bff",
      "type": "color"
    },
    "background": {
      "value": "#f8f9fa",
      "type": "color"
    }
  }
}

// 📄 style-dictionary.config.js
module.exports = {
  source: ["tokens/**/*.json"],
  platforms: {
    css: {
      transformGroup: "css",
      buildPath: "build/css/",
      files: [{
        destination: "variables.css",
        format: "css/variables"
      }]
    },
    js: {
      transformGroup: "js",
      buildPath: "build/js/",
      files: [{
        destination: "tokens.js",
        format: "javascript/es6"
      }]
    }
  }
};

// 📄 src/Button.jsx
import React from 'react';
import '../build/css/variables.css';

export const Button = ({ children }) => {
  return (
    <button style={{
      backgroundColor: 'var(--color-primary)',
      color: '#fff',
      padding: '0.5rem 1rem',
      border: 'none',
      borderRadius: '4px'
    }}>
      {children}
    </button>
  );
};

// 📄 .gitignore
node_modules/
build/
.env

// 📄 package.json
{
  "name": "design-system",
  "scripts": {
    "build": "style-dictionary build",
    "start": "vite"
  },
  "devDependencies": {
    "style-dictionary": "^3.9.2"
  },
  "dependencies": {
    "react": "^18.0.0",
    "react-dom": "^18.0.0"
  }
}

// 📄 README.md
# Design System (No Storybook)

- 🎨 Design Tokens → `tokens/`
- 🧪 Build Tokens → `npm run build`
- 🧵 Use Tokens in React via `var(--color-primary)`
- 📚 Style Dictionary 자동 변환 시스템

## 연동 흐름
Figma → (JSON export) → tokens → Style Dictionary → React CSS 적용
