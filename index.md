---
layout: page
---

# 关于我

<img src="/images/sphoneshot_beam_bnw.png" class="floatpic">

哈喽，这里是**刘家华 (James Liu)**的个人主页，这里记录了我的专业学习思考、算法刷题心得与项目实践过程。<br>

立志于成为一名兼具理论基础与工程能力的开发者！<br>

🎓 本人现就读于**南开大学**[计算机学院](https://cc.nankai.edu.cn)的计算机科学与技术专业（2025级）。

📌 目前专注于深度学习基础下的**计算机视觉（CV）**相关课题研究，技术小白正在持续学习进步ing...<br>

💻 常用语言以**C++**与**Python**为主，并拥有**GPT-5.6 Sol**作为第二大脑😄。
## 工作经历

<div class="timeline">
  <div class="timeline-progress" id="timeline-progress"></div>
  <div class="timeline-item">
      <div class="timeline-dot" style="background: #ffffff;">
        <img src="/images/logo/class4.png" alt="Class4">
      </div>
      <div class="timeline-card">
        <div class="timeline-header">
          <div class="timeline-role">文体委员 <span class="timeline-sep">|</span> <span class="timeline-company">计算机科学与技术4班</span></div>
          <span class="timeline-time">Sept. 2026 - Present</span>
        </div>
        <div class="timeline-details">
          负责班级文体活动的策划、预算编制与现场落地，对接学院团委与班级同学，高效完成信息下达与场地、物资等资源的筹备调度。同时，关注同学课余文化生活，通过丰富活动形式提升班级内部的沟通频度与团队凝聚力。通过定期的意向调研与活动反馈，建立良好的班级沟通渠道，兼顾不同同学的参与需求。
        </div>
      </div>
    </div>
  <div class="timeline-item timeline-item--current">
    <div class="timeline-dot" style="background: #ffffff;">
      <img src="/images/logo/nkcs.JPG" alt="南开大学计算机学院">
    </div>
    <div class="timeline-card">
      <div class="timeline-header">
        <div class="timeline-role">学生权益发展部干事<span class="timeline-sep">|</span> <span class="timeline-company">南开大学计算机学院学生会</span></div>
        <span class="timeline-time">Sept. 2025 - Sept. 2026</span>
      </div>
      <div class="timeline-details">
      在学生会学生权益发展部的工作中曾参与策划和组织二十四节气主题活动，组织各部员搭建学生与学校交流的平台，实现各方面的良性沟通；同时，配合学院其他团学组织参与承接学生活动的后勤保障和线下组织工作；定期收集学院内师生权益相关意见，联合学生会其他部门共同促进问题的解决，保障学生权益。
      </div>
    </div>
  </div>



  <div class="timeline-item">
    <div class="timeline-dot" style="background: #ffffff;">
      <img src="/images/logo/hfyz.png" alt="合肥一中">
    </div>
    <div class="timeline-card">
      <div class="timeline-header">
        <div class="timeline-role">信息学竞赛校队队员 <span class="timeline-sep">|</span> <span class="timeline-company">合肥市第一中学</span></div>
        <span class="timeline-time">Oct. 2022 - Jun. 2023</span>
      </div>
      <div class="timeline-details">
        曾作为校信息学竞赛队队员，接受过系统化的 C++ 编程与算法思维训练。具备独立分析复杂问题并将其转化为高效代码的能力，具备良好的逻辑严谨度与抗压能力。
      </div>
    </div>
  </div>

</div>

<script>
(function() {
  var timelineProgress = document.getElementById('timeline-progress');
  var timeline = document.querySelector('.timeline');
  if (!timelineProgress || !timeline) return;

  var items = timeline.querySelectorAll('.timeline-item');

  // IntersectionObserver for in-view class
  if ('IntersectionObserver' in window) {
    var observer = new IntersectionObserver(function(entries) {
      entries.forEach(function(entry) {
        if (entry.isIntersecting) {
          entry.target.classList.add('in-view');
        }
      });
    }, { rootMargin: '0px 0px -15% 0px' });

    items.forEach(function(item, idx) {
      if (idx < 3) {
        // Reveal first 3 immediately on load (still gets the stagger transition)
        item.classList.add('in-view');
      } else {
        observer.observe(item);
      }
    });
  } else {
    items.forEach(function(item) { item.classList.add('in-view'); });
  }

  // Scroll progress bar
  window.addEventListener('scroll', function() {
    var rect = timeline.getBoundingClientRect();
    var totalHeight = timeline.offsetHeight;
    var windowH = window.innerHeight;
    var lineTop = 30;
    var lineBottom = 30;
    var lineHeight = totalHeight - lineTop - lineBottom;

    if (rect.top < windowH && rect.bottom > 0) {
      var scrolled = Math.min(1, Math.max(0, (windowH - rect.top - lineTop) / (totalHeight - lineTop + windowH * 0.4)));
      timelineProgress.style.height = Math.min(scrolled * lineHeight, lineHeight) + 'px';
    }
  }, { passive: true });
})();
</script>

欢迎与各位优秀的同学们一起交流、学习、进步。如果对我感兴趣，寻求更进一步的共同探索，请通过南开大学飞书联系我，或发送email至 - JiahuaLiu_edu@foxmail.com

**<font color="#990000">期待与优秀的计算机视觉方向的导师沟通合作！</font>**
