# 🎨 디자인 시스템 구축 가이드 (Without Storybook)

디자인 시스템을 간결하고 체계적으로 관리하기 위해  
Figma 디자인 → Style Dictionary → React → Git 흐름으로 정리된  
**가벼운 토큰 기반 디자인 시스템 템플릿**입니다.

---

## 📁 디렉토리 구조
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


단계
도구
디자인 → 토큰
Figma + Tokens Studio Plugin
토큰 관리
Style Dictionary
React 적용
CSS 변수 or JS import
Git 관리
Git + Conventional Commits
문서화 (선택)
Notion or Zeroheight 링크

