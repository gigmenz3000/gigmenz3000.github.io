<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Репетитор по математике</title>
<style>
  :root{
    --blue:#4d7cf0;
    --blue-dark:#3a63d6;
    --text:#1f2430;
    --muted:#6b7280;
    --bg-cream:#faf7f1;
    --border:#e7e3da;
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  body{
    font-family:'Segoe UI', Arial, sans-serif;
    color:var(--text);
    line-height:1.5;
  }
  a{text-decoration:none;color:inherit;}
  a[href^="tel:"]{cursor:pointer;}
  a[href^="tel:"]:hover{color:var(--blue);text-decoration:underline;}
  .container{max-width:1100px;margin:0 auto;padding:0 24px;}

  /* Header */
  header{
    display:flex;justify-content:space-between;align-items:center;
    padding:24px 0;
  }
  header nav{display:flex;gap:32px;font-weight:500;}
  header nav a{color:var(--text);opacity:.85;}
  header nav a:hover{opacity:1;color:var(--blue);}
  .contact-info{text-align:right;font-size:14px;color:var(--muted);}
  .contact-info strong{display:block;color:var(--text);font-size:15px;}

  /* Hero */
  .hero{
    display:grid;grid-template-columns:1fr 1fr;gap:48px;
    align-items:center;padding:48px 0 80px;
  }
  .hero-photo{
    background:linear-gradient(135deg,#dbe6ff,#f3f0ff);
    border-radius:16px;
    height:420px;
    display:flex;align-items:center;justify-content:center;
    position:relative;overflow:hidden;
  }
  .hero-photo svg{width:70%;height:70%;}
  .hero h1{
    font-size:38px;line-height:1.25;font-weight:700;margin-bottom:18px;
  }
  .hero p{color:var(--muted);font-size:16px;margin-bottom:28px;max-width:480px;}
  .hero p strong{color:var(--text);}
  .btn{
    display:inline-block;background:var(--blue);color:#fff;
    padding:14px 28px;border-radius:8px;font-weight:600;
    transition:background .2s;
  }
  .btn:hover{background:var(--blue-dark);}

  /* Info cards (Образование/Опыт style) */
  .info-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:40px 60px;
    padding-bottom:80px;
  }
  .info-card{display:flex;gap:20px;}
  .info-icon{
    flex-shrink:0;width:56px;height:56px;border-radius:50%;
    border:2px solid var(--blue);display:flex;align-items:center;justify-content:center;
  }
  .info-card h3{font-size:18px;margin-bottom:10px;}
  .info-card ul{color:var(--muted);font-size:14.5px;padding-left:18px;}
  .info-card li{margin-bottom:4px;}
  .info-card p{color:var(--muted);font-size:14.5px;}

  /* Problems section */
  .section-cream{
    background:var(--bg-cream);
    padding:70px 0;
  }
  .section-title{
    text-align:center;font-size:30px;font-weight:700;margin-bottom:40px;
  }
  .accordion{max-width:650px;margin:0 auto;}
  .acc-item{
    background:#fff;border:1px solid var(--border);border-radius:6px;
    margin-bottom:12px;padding:0 24px;
    transition:border-color .2s;
  }
  .acc-item.open{border-color:var(--text);border-width:2px;}
  .acc-header{
    display:flex;justify-content:space-between;align-items:center;
    cursor:pointer;padding:18px 0;font-weight:600;
  }
  .acc-item span.plus{
    color:var(--blue);font-size:20px;font-weight:300;
    width:32px;height:32px;border-radius:50%;
    display:flex;align-items:center;justify-content:center;
    transition:background .2s,color .2s;
  }
  .acc-item.open span.plus{background:var(--blue);color:#fff;}
  .acc-body{
    max-height:0;overflow:hidden;color:var(--muted);font-size:14.5px;
    transition:max-height .25s ease, padding .25s ease;
  }
  .acc-item.open .acc-body{max-height:200px;padding-bottom:20px;}

  /* Services */
  .services{padding:70px 0;}
  .services-grid{
    display:grid;grid-template-columns:1fr 1fr;gap:36px 60px;
    max-width:900px;margin:0 auto;
  }
  .service{border-bottom:1px solid var(--border);padding-bottom:20px;}
  .service-top{display:flex;justify-content:space-between;font-weight:700;font-size:17px;margin-bottom:8px;}
  .service-top .price{color:var(--blue);}
  .service p{color:var(--muted);font-size:14.5px;}

  /* Reviews */
  .reviews{background:var(--bg-cream);padding:70px 0;position:relative;}
  .review-wrap{display:flex;align-items:center;justify-content:center;gap:36px;max-width:850px;margin:0 auto;position:relative;}
  .avatar{
    width:90px;height:90px;border-radius:50%;flex-shrink:0;
    background:linear-gradient(135deg,#9bb6ff,#c9b8ff);
    display:flex;align-items:center;justify-content:center;
    color:#fff;font-weight:700;font-size:28px;
  }
  .review-text p{font-size:16px;color:var(--text);margin-bottom:14px;}
  .review-text strong{font-size:14.5px;}
  .dots{display:flex;justify-content:center;gap:8px;margin-top:24px;}
  .dot{width:8px;height:8px;border-radius:50%;background:#cbd0db;}
  .dot.active{background:var(--blue);}
  .nav-btn{
    width:40px;height:40px;border-radius:50%;background:var(--blue);
    color:#fff;display:flex;align-items:center;justify-content:center;
    border:none;cursor:pointer;font-size:18px;flex-shrink:0;
  }
  .nav-btn.outline{background:transparent;border:2px solid var(--text);color:var(--text);}

  /* Footer / contacts */
  footer{padding:50px 0;text-align:center;color:var(--muted);font-size:14px;}
  footer strong{color:var(--text);}

  @media (max-width:760px){
    .hero, .info-grid, .services-grid{grid-template-columns:1fr;}
    header{flex-direction:column;gap:16px;text-align:center;}
    header nav{flex-wrap:wrap;justify-content:center;gap:16px;}
    .review-wrap{flex-direction:column;text-align:center;}
    .nav-btn{display:none;}
  }
</style>
</head>
<body>

<header class="container">
  <nav>
    <a href="#about">Обо мне</a>
    <a href="#services">Услуги и цены</a>
    <a href="#contacts">Контакты</a>
  </nav>
  <div class="contact-info">
    <strong><a href="tel:+79601850730">+7 960 185 07 30</a></strong>
    Москва, дистанционно
  </div>
</header>

<section class="hero container" id="about">
  <div class="hero-photo">
    <svg viewBox="0 0 200 200" fill="none">
      <circle cx="100" cy="100" r="90" fill="#fff" opacity="0.5"/>
      <text x="100" y="120" font-size="90" text-anchor="middle" fill="#4d7cf0" font-family="Georgia, serif">∑</text>
    </svg>
  </div>
  <div>
    <h1>Репетитор по математике<br>с опытом более 5 лет</h1>
    <p>Я — <strong>Крылов Степан</strong>, преподаватель математики. Готовлю учеников к ЕГЭ и ОГЭ, помогаю разобраться в школьной программе и повысить успеваемость. Объясняю сложные темы простым языком, без лишней зубрёжки.</p>
    <a href="https://t.me/KiRiTo12_2" target="_blank" class="btn">Записаться на пробное занятие</a>
  </div>
</section>

<section class="container info-grid">
  <div class="info-card">
    <div class="info-icon">🎓</div>
    <div>
      <h3>Образование</h3>
      <ul>
        <li>Окончил МГУ им. М.В. Ломоносова, факультет вычислительной математики и кибернетики</li>
        <li>Дополнительно прошёл курсы повышения квалификации по методике подготовки к ЕГЭ/ОГЭ</li>
      </ul>
    </div>
  </div>
  <div class="info-card">
    <div class="info-icon">📜</div>
    <div>
      <h3>Сертификаты</h3>
      <ul>
        <li>Сертификат эксперта ЕГЭ по математике (профильный уровень)</li>
        <li>Диплом о профессиональной переподготовке «Методика преподавания математики»</li>
      </ul>
    </div>
  </div>
  <div class="info-card">
    <div class="info-icon">💬</div>
    <div>
      <h3>Опыт</h3>
      <ul>
        <li>Работал учителем математики в школе на протяжении 3 лет</li>
        <li>Более 5 лет провожу индивидуальные занятия с учениками 5–11 классов</li>
      </ul>
    </div>
  </div>
  <div class="info-card">
    <div class="info-icon">📚</div>
    <div>
      <h3>Результаты учеников</h3>
      <p>Средний балл ЕГЭ моих учеников — 82+. Более 150 успешно подготовленных к экзаменам школьников за время практики.</p>
    </div>
  </div>
</section>

<section class="section-cream">
  <h2 class="section-title">Какие задачи решаю</h2>
  <div class="accordion container">
    <div class="acc-item" data-text="Биполярные расстройства характеризуются чередованием эпизодов мании и депрессии. В обучении это часто проявляется как нестабильная концентрация: ученику то легко даются сложные темы, то трудно удержать внимание даже на простых задачах. Подбираю темп занятий и формат подачи материала с учётом текущего состояния.">
      <div class="acc-header"><span>Сложности с концентрацией внимания</span><span class="plus">+</span></div>
      <div class="acc-body"></div>
    </div>
    <div class="acc-item" data-text="Многие ученики боятся математики из-за прошлых неудач и низких оценок. Такой страх мешает спокойно воспринимать новый материал и решать задачи на экзамене. Работаю над тем, чтобы вернуть уверенность: начинаем с понятных и достижимых задач, постепенно увеличивая сложность.">
      <div class="acc-header"><span>Страх перед математикой и низкая уверенность в себе</span><span class="plus">+</span></div>
      <div class="acc-body"></div>
    </div>
    <div class="acc-item" data-text="Перед контрольными и экзаменами у учеников часто возникает паника, из-за которой даже хорошо выученный материал «выпадает из головы». Разбираем типовые варианты заданий, тренируем тайминг и алгоритмы решения, чтобы на экзамене не было неожиданностей.">
      <div class="acc-header"><span>Тревога перед контрольными и экзаменами</span><span class="plus">+</span></div>
      <div class="acc-body"></div>
    </div>
    <div class="acc-item" data-text="Пробелы в базовых темах накапливаются годами и мешают усваивать новый материал. Провожу диагностику, нахожу конкретные темы, которые «потерялись», и закрываю их в первую очередь — это даёт быстрый рост успеваемости.">
      <div class="acc-header"><span>Пробелы в базовых темах прошлых лет</span><span class="plus">+</span></div>
      <div class="acc-body"></div>
    </div>
    <div class="acc-item" data-text="Отсутствие мотивации к учёбе часто связано не с ленью, а с непонятностью предмета и отсутствием видимого результата. Выстраиваю занятия так, чтобы ученик видел свой прогресс на каждом этапе — это возвращает интерес к предмету.">
      <div class="acc-header"><span>Низкая мотивация к учёбе</span><span class="plus">+</span></div>
      <div class="acc-body"></div>
    </div>
  </div>
</section>

<section class="services container" id="services">
  <h2 class="section-title">Услуги и цены</h2>
  <div class="services-grid">
    <div class="service">
      <div class="service-top"><span>Пробное занятие</span><span class="price">500 ₽</span></div>
      <p>Знакомство, диагностика текущего уровня знаний и определение пробелов в теме</p>
    </div>
    <div class="service">
      <div class="service-top"><span>Подготовка к ОГЭ</span><span class="price">2000 ₽</span></div>
      <p>Системная подготовка по всем разделам ОГЭ с разбором реальных вариантов</p>
    </div>
    <div class="service">
      <div class="service-top"><span>Подготовка к ЕГЭ (база)</span><span class="price">2000 ₽</span></div>
      <p>Уверенное закрытие базового уровня ЕГЭ для получения нужного балла</p>
    </div>
    <div class="service">
      <div class="service-top"><span>Подготовка к ЕГЭ (профиль)</span><span class="price">2500 ₽</span></div>
      <p>Глубокая подготовка к профильному ЕГЭ, включая задания части 2</p>
    </div>
    <div class="service">
      <div class="service-top"><span>Повышение успеваемости</span><span class="price">1800 ₽</span></div>
      <p>Помощь с текущей школьной программой, разбор домашних заданий и контрольных</p>
    </div>
    <div class="service">
      <div class="service-top"><span>Интенсив перед экзаменом</span><span class="price">от 9000 ₽</span></div>
      <p>Курс из нескольких занятий для быстрого закрытия пробелов перед экзаменом</p>
    </div>
  </div>
</section>

<section class="reviews">
  <h2 class="section-title">Отзывы</h2>
  <div class="review-wrap">
    <button class="nav-btn outline">&#8249;</button>
    <div class="avatar">МК</div>
    <div class="review-text">
      <p>Сын никак не мог разобраться с тригонометрией, а после трёх занятий с Андреем тема стала понятной. Объясняет терпеливо, всегда находит способ объяснить по-другому, если что-то не понятно с первого раза. Очень рекомендую!</p>
      <strong>Марина Ковалёва</strong>
    </div>
    <button class="nav-btn">&#8250;</button>
  </div>
  <div class="dots">
    <span class="dot active"></span>
    <span class="dot"></span>
    <span class="dot"></span>
  </div>
</section>

<footer id="contacts" class="container">
  <p><strong>Крылов Степан</strong> — репетитор по математике</p>
  <p><a href="tel:+79601850730">+7 960 185 07 30</a> · Москва, дистанционно</p>
</footer>

<script>
  // Accordion toggle
  document.querySelectorAll('.acc-item').forEach(item=>{
    const body = item.querySelector('.acc-body');
    body.textContent = item.dataset.text;
    item.querySelector('.acc-header').addEventListener('click',()=>{
      const isOpen = item.classList.contains('open');
      document.querySelectorAll('.acc-item').forEach(i=>{
        i.classList.remove('open');
        i.querySelector('.plus').textContent = '+';
      });
      if(!isOpen){
        item.classList.add('open');
        item.querySelector('.plus').textContent = '×';
      }
    });
  });

  // Reviews carousel
  const reviews = [
    {initials:'МК', text:'Сын никак не мог разобраться с тригонометрией, а после трёх занятий со Степаном тема стала понятной. Объясняет терпеливо, всегда находит способ объяснить по-другому, если что-то не понятно с первого раза. Очень рекомендую!', name:'Марина Ковалёва'},
    {initials:'ДС', text:'Готовился к профильному ЕГЭ почти год со Степаном — поднял балл с 40 до 86. Занятия всегда структурированные, домашка по делу, разбор ошибок подробный. Без этой подготовки точно бы не поступил туда, куда хотел.', name:'Денис Соколов'},
    {initials:'ОП', text:'Дочка отставала по геометрии и боялась контрольных. Сейчас сама решает задачи и не паникует перед уроком. Степан умеет находить подход к ребёнку, занятия проходят легко и без стресса.', name:'Ольга Петрова'}
  ];
  let current = 0;
  const avatar = document.querySelector('.avatar');
  const text = document.querySelector('.review-text p');
  const name = document.querySelector('.review-text strong');
  const dots = document.querySelectorAll('.dot');
  function render(){
    avatar.textContent = reviews[current].initials;
    text.textContent = reviews[current].text;
    name.textContent = reviews[current].name;
    dots.forEach((d,i)=>d.classList.toggle('active', i===current));
  }
  document.querySelector('.nav-btn.outline').addEventListener('click',()=>{
    current = (current - 1 + reviews.length) % reviews.length; render();
  });
  document.querySelector('.nav-btn:not(.outline)').addEventListener('click',()=>{
    current = (current + 1) % reviews.length; render();
  });
  dots.forEach((d,i)=>d.addEventListener('click',()=>{current=i; render();}));
</script>

</body>
</html>

