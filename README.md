# tanchugonggao
## 给自己的静态页面添加一个弹出公告，提醒访客你的重要通知，增加黏性
**这个弹窗公告适合用于需要简单提醒、重要公告或优惠活动等场景，视觉效果温和，用户体验良好，并能较好地吸引用户注意力。**
很高兴这个公告效果达到了您的需求！以下是这个公告弹窗的作用、功能以及结构的详细介绍。

### 1. **作用**
这个公告弹窗用于在用户访问静态导航页时，以视觉上温和顺畅的方式弹出一条重要通知或信息。通过居中的弹窗和半透明的背景，公告内容可以快速吸引用户注意，同时不会显得突兀。用户可以阅读公告内容，了解相关信息，然后点击关闭按钮来关闭公告。

### 2. **功能**
- **自动弹出**：公告会在页面加载完成后自动弹出，以确保用户可以第一时间看到信息。
- **内容自定义**：公告标题、正文内容的文字大小和颜色都可以通过CSS轻松调整，适应不同的设计需求。
- **关闭按钮**：公告框下方居中的“关闭”按钮放在小容器内，显得直观醒目。按钮点击后，公告会顺畅地关闭，避免打扰用户的体验。
- **居中显示**：公告使用CSS `flex`布局，使其在页面的水平方向和垂直方向都居中，适应不同的屏幕尺寸。
- **温和的弹出/关闭效果**：CSS动画使公告弹出和关闭过程平滑，视觉体验流畅。

### 3. **结构**
这个公告由以下结构组成：

- **HTML结构**
  - 外层`<div>`使用`announcement-modal`类，提供整个弹窗的背景遮罩。
  - 内部的`announcement-content`是实际显示公告内容的容器。
  - `<h2>`标签用于公告标题，`<p>`标签用于显示正文内容。
  - `close-container`容器内嵌`close-btn`，用于显示“关闭”按钮并处理用户关闭弹窗的需求。

- **CSS样式**
  - **.announcement-modal**：设置弹窗遮罩的背景颜色、透明度和全屏覆盖，并使用`flex`布局将内容居中。
  - **.announcement-content**：用于定义公告框的样式，包括宽度、背景颜色、阴影效果以及圆角边框。动画效果为`scale`和`opacity`结合，提升视觉体验。
  - **.close-container** 和 **.close-btn**：居中显示“关闭”按钮，并通过背景色和文字样式使其醒目，且按钮在用户悬停时会有颜色变化以增加交互感。

- **JavaScript交互**
  - `openAnnouncementPopup()` 函数用于显示弹窗，`closeAnnouncementPopup()` 函数则用于隐藏弹窗。
  - 页面加载后，JavaScript会自动打开弹窗，并为关闭按钮绑定点击事件，确保点击后公告能关闭。




### HTML
```html
<div id="announcementPopup" class="announcement-modal">
  <div class="announcement-content">
    <h2>公告标题</h2>
    <p>这是公告内容，可以根据需要自定义字体颜色和大小。搜索我的名字你会得到很多惊喜。</p>
    <div class="close-container">
      <span class="close-btn">关闭</span>
    </div>
  </div>
</div>
```

### CSS
```css
/* 弹窗背景 */
.announcement-modal {
  display: none; /* 初始隐藏 */
  position: fixed;
  z-index: 1000;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4); /* 半透明背景 */
  display: flex;
  align-items: center; /* 垂直居中 */
  justify-content: center; /* 水平居中 */
}

/* 弹窗内容框 */
.announcement-content {
  position: relative;
  padding: 20px;
  width: 70%; /* 可根据需要调整宽度 */
  max-width: 600px;
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.2);
  text-align: center;
  animation: smoothPopup 0.5s ease; /* 弹出效果 */
}

/* 标题和内容文字样式 */
.announcement-content h2 {
  font-size: 1.5em;
  color: #333;
}

.announcement-content p {
  font-size: 1em;
  color: #666;
}

/* 关闭按钮容器 */
.close-container {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}

/* 关闭按钮样式 */
.close-btn {
  font-size: 1em;
  color: #fff;
  background-color: #333;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  text-align: center;
}

.close-btn:hover {
  background-color: #555;
}

/* 弹出和关闭的动画效果 */
@keyframes smoothPopup {
  from { transform: scale(0.9); opacity: 0; }
  to { transform: scale(1); opacity: 1; }
}
```

### JavaScript
```// 页面加载时自动弹出公告
window.onload = function() {
  openAnnouncementPopup();
  
  // 获取关闭按钮并绑定点击事件
  const closeButton = document.querySelector(".close-btn");
  closeButton.addEventListener("click", closeAnnouncementPopup);
};

// 打开公告弹窗
function openAnnouncementPopup() {
  const popup = document.getElementById("announcementPopup");
  popup.style.display = "flex";
}

// 关闭公告弹窗
function closeAnnouncementPopup() {
  const popup = document.getElementById("announcementPopup");
  popup.style.display = "none";
}

```


