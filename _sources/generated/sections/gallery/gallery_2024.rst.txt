2024 Gallery
===========

.. raw:: html

   <style>
   .gallery-container {
       display: grid;
       grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
       gap: 20px;
       padding: 20px;
   }
   .gallery-item {
       border: 1px solid #ddd;
       border-radius: 8px;
       overflow: hidden;
       box-shadow: 0 2px 5px rgba(0,0,0,0.1);
   }
   .gallery-item img {
       width: 100%;
       height: 200px;
       object-fit: cover;
   }
   .gallery-item .content {
       padding: 15px;
   }
   .gallery-item .title {
       font-weight: bold;
       margin-bottom: 10px;
   }
   .gallery-item .description {
       font-size: 0.9em;
       color: #666;
   }
   .video-container {
       position: relative;
       padding-bottom: 56.25%;
       height: 0;
       overflow: hidden;
       margin-bottom: 20px;
   }
   .video-container iframe {
       position: absolute;
       top: 0;
       left: 0;
       width: 100%;
       height: 100%;
   }
   </style>

.. raw:: html

   <div class="gallery-container">
   <!-- 갤러리 아이템 예시 -->
   <div class="gallery-item">
       <img src="_images/placeholder.jpg" alt="이미지 설명">
       <div class="content">
           <div class="title">이미지 제목</div>
           <div class="description">이미지에 대한 설명이 들어갈 자리입니다.</div>
       </div>
   </div>
   </div>

.. raw:: html

   <div class="video-container">
   <iframe src="https://www.youtube.com/embed/VIDEO_ID" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
   </div>
