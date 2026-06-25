# Deadline Manager v1.0

## 上傳 GitHub Pages
1. 把整個資料夾內的檔案上傳到 GitHub repository 根目錄。
2. 確認根目錄有 `index.html`、`css/`、`js/`、`manifest.json`、`service-worker.js`。
3. Settings → Pages → Deploy from branch → main / root。

## Firebase 已內建
已使用目前提供的 firebaseConfig。
Firestore Rules 需為：

```js
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

## 資料位置
`users/{uid}/app/state`

包含 brands、projects、categories、tasks、settings。
