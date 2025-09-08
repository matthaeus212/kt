# 🎨 디자인 시스템 구축 가이드

디자인 시스템을 간결하고 체계적으로 관리하기 위해  
Figma 디자인 → Style Dictionary → React → Git 흐름으로 정리된  
**토큰 기반 디자인 시스템 템플릿**입니다.

---

## 📁 디렉토리 구조

```
design-system/
├─ tokens/               # 디자인 토큰 JSON
│  └─ color.json
├─ build/                # Style Dictionary 결과물
│  ├─ css/
│  └─ js/
├─ src/                  # React 컴포넌트
│  └─ Button.jsx
├─ style-dictionary.config.js
├─ package.json
├─ .gitignore
└─ README.md
```

## 🎨 1. 디자인 토큰 정의

`tokens/color.json`

```json
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
```

---

## ⚙️ 2. Style Dictionary 설정

`style-dictionary.config.js`

```js
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
```

---

## 🔧 3. 빌드 실행

```bash
npx style-dictionary build
```

---

## 🧪 4. React에서 사용

`src/Button.jsx`

```jsx
import React from 'react';
import '../build/css/variables.css';

export const Button = ({ children }) => (
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
```

---

## 🌱 5. Git 형상관리

```bash
git init
git remote add origin https://github.com/your-org/design-system.git
git add .
git commit -m "init: 디자인 토큰 및 설정 추가"
git push -u origin main
```


## 📚 프로세스 요약

| 단계 | 도구 |
|------|------|
| 디자인 → 토큰 | Figma + Tokens Studio Plugin |
| 토큰 관리 | Style Dictionary |
| React 적용 | CSS 변수 or JS import |
| Git 관리 | Git + Conventional Commits |
| 문서화 (선택) | Notion or Zeroheight 링크 |

---


