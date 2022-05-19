# setup
vscode, github

## 👩‍💻 setup vscode 

Badge | URL
------------ | -------------
<img src="https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB" /> | <a href="https://github.com/sing3demons/vscode-react/blob/main/README.md"> React - setup vscode </a> 
<img src="https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vue-dot-js&logoColor=4FC08D" /> | <a href="https://github.com/sing3demons/vscode-vue/blob/main/README.md">Vue - setup vscode</a>
 <a href="https://github.com/sing3demons/awesome-go"> <img src="https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white" /> </a> | <a href="https://github.com/sing3demons/go-docker-mysql/blob/main/README.md">go - docker - mysql</a>
<a href="https://github.com/sing3demons/awesome-dotnet"> <img src="https://img.shields.io/badge/.NET-5C2D91?style=for-the-badge&logo=dot-net&logoColor=white" /> </a> | <a href="https://github.com/sing3demons/dotnet-setup/blob/main/README.md">dotnet - docker</a>

<br/>
## git commit -m 
- feat (✨): ฟีเจอร์ใหม่ 
- fix (🐛): แก้ไขบัค
- refactor (📦): ปรับโครงสร้าง​ (ไม่ได้เพิ่มฟีเจอร์ แต่ก็ไม่ได้แก้บัค)
- style (💎): การแก้ไขโค้ดที่ไม่ได้เปลี่ยนแปลงความหมาย เช่น เติม semicolon, ลบ whitespace
- test (🚨): เพิ่ม/แก้ไข Test
- perf (🚀): ปรับปรุงประสิทธิภาพการทำงาน
- build (🔨): การแก้ไขที่กระทบกระบวนการ Build
- ci (⚙️): ปรับการตั้งค่า CI เช่น ปรับขั้นตอนการทำงานของ GitHub Actions
- docs (📚): การแก้ไขที่เกี่ยวกับเอกสาร เช่น แก้ README

### วิธีใช้งานก็แค่เติมนำหน้า Commit Message ไปเลย เช่น:

```
feat: add confirmation dialog on delete
```
```
fix: isOdd returns true when input is 0
```
```
refactor: remove unnecessary else after return
```
<br/>

<hr>
### Setup vscode React  ![](https://img.shields.io/badge/Code-React-informational?style=flat&logo=react&logoColor=white&color=6aa6f8)

cmd + shift + p > Preferences: Open Workspace Settings (JSON)

#### setting.json
```json
{
  "editor.formatOnSave": true,
  "emmet.syntaxProfiles": { "javascript": "jsx" },
  "emmet.includeLanguages": { "javascript": "javascriptreact" },
  "emmet.triggerExpansionOnTab": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "[javascript]": { "editor.defaultFormatter": "esbenp.prettier-vscode" }
}
```
<br>

```
touch .prettierrc
```

```json
{ 
"semi": false, 
"singleQuote": true 
}
```

#### esLint
```
touch .eslintrc
```
```
{
  "extends": ["react-app", "plugin:prettier/recommended"]
}
```
```
yarn add -D eslint-plugin-prettier eslint-config-prettier prettier
```

<hr>
