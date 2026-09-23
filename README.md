<!DOCTYPE html><!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>TEAM JTB</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Black+Han+Sans&family=IBM+Plex+Sans+KR:wght@400;600&display=swap" rel="stylesheet">
<style>
  /* ===== 색상: 여기 값만 바꾸면 전체 색이 바뀌어요 ===== */
  :root {
    --steel-light: #eef1f4;
    --steel: #c9ced3;
    --steel-dark: #5b636b;
    --ink: #1c2430;
    --red: #d7263d;      /* 포장마차 빨간 의자색 */
    --paper: #f7f8f9;
  }

  * { box-sizing: border-box; }
  body {
    margin: 0;
    background: var(--paper);
    color: var(--ink);
    font-family: "IBM Plex Sans KR", "Apple SD Gothic Neo", "Malgun Gothic", sans-serif;
    line-height: 1.7;
  }

  /* ===== 상단 메뉴 ===== */
  header {
    position: sticky; top: 0; z-index: 10;
    display: flex; align-items: center; justify-content: space-between;
    gap: 1rem; flex-wrap: wrap;
    padding: 0.9rem clamp(1rem, 4vw, 3rem);
    background: rgba(247, 248, 249, 0.92);
    backdrop-filter: blur(8px);
    border-bottom: 2px solid var(--steel);
  }
  .logo {
    font-family: "Black Han Sans", sans-serif;
    font-size: 1.6rem; letter-spacing: 0.02em;
    background: none; border: 0; padding: 0; color: var(--ink); cursor: pointer;
  }
  nav { display: flex; gap: 0.4rem; flex-wrap: wrap; }
  nav button {
    font: inherit; font-weight: 600; font-size: 0.95rem;
    padding: 0.45rem 1rem;
    border: 2px solid var(--ink); border-radius: 999px;
    background: transparent; color: var(--ink); cursor: pointer;
    transition: background 0.15s, color 0.15s;
  }
  nav button:hover { background: var(--steel-light); }
  nav button[aria-current="page"] { background: var(--red); border-color: var(--red); color: #fff; }
  button:focus-visible { outline: 3px solid var(--red); outline-offset: 3px; }

  main { max-width: 1040px; margin: 0 auto; padding: clamp(2rem, 6vw, 4rem) clamp(1rem, 4vw, 3rem); }
  .view[hidden] { display: none; }
  .view { animation: appear 0.35s ease-out; }
  @keyframes appear { from { opacity: 0; transform: translateY(8px); } to { opacity: 1; transform: none; } }

  h1, h2 { font-family: "Black Han Sans", sans-serif; font-weight: 400; line-height: 1.15; margin: 0 0 1rem; }
  h2 { font-size: clamp(2rem, 5vw, 3rem); }

  /* ===== 홈: 양푼 ===== */
  .hero { display: grid; grid-template-columns: minmax(0, 1fr) minmax(0, 1fr); gap: clamp(2rem, 5vw, 4rem); align-items: center; }
  .bowl {
    position: relative; width: 100%; max-width: 440px; aspect-ratio: 1; margin: 0 auto;
    border-radius: 50%; border: 0; padding: 0; cursor: pointer;
    background: radial-gradient(circle,
      #f4f6f8 0 36%, #d6dbe0 37% 50%, #a9b1b8 51% 60%,
      #e4e8eb 61% 68%, #7d868f 69% 71%, #cfd4d9 72% 100%);
    box-shadow: inset 0 -18px 40px rgba(28,36,48,0.25), 0 24px 40px -20px rgba(28,36,48,0.45);
    overflow: hidden;
  }
  /* 스테인리스 광택 (클릭하면 휘저어짐) */
  .bowl::before {
    content: ""; position: absolute; inset: 0; border-radius: 50%;
    background: conic-gradient(from 30deg, rgba(255,255,255,0.7), transparent 12%, transparent 40%,
      rgba(255,255,255,0.45) 52%, transparent 64%, transparent 90%, rgba(255,255,255,0.7));
    mix-blend-mode: soft-light;
    transition: transform 1.2s cubic-bezier(.2,.7,.2,1);
  }
  .bowl.stirred::before { transform: rotate(720deg); }
  .bowl-title {
    position: absolute; inset: 0; display: grid; place-content: center; text-align: center;
    font-family: "Black Han Sans", sans-serif; color: var(--ink);
    font-size: clamp(2.6rem, 8vw, 4.4rem); line-height: 0.95;
  }
  .bowl-title small { display: block; font-family: "IBM Plex Sans KR", sans-serif; font-size: 0.8rem; font-weight: 600; color: var(--steel-dark); margin-top: 0.8rem; }

  .slogan { font-size: clamp(1.3rem, 3vw, 1.7rem); font-weight: 600; line-height: 1.35; margin: 0 0 1.5rem; }
  .intro p { max-width: 60ch; margin: 0 0 1rem; }
  .code-list { list-style: none; padding: 0; margin: 1.5rem 0; border-left: 4px solid var(--red); }
  .code-list li { padding: 0.35rem 0 0.35rem 1rem; font-weight: 600; }
  .signoff { font-family: "Black Han Sans", sans-serif; font-size: 1.5rem; color: var(--red); margin-top: 1.5rem; }

  /* ===== 공지 ===== */
  .notice { display: grid; grid-template-columns: 7rem 1fr; gap: 1rem; padding: 1.2rem 0; border-top: 2px solid var(--steel); }
  .notice:last-child { border-bottom: 2px solid var(--steel); }
  .notice time { font-family: "Black Han Sans", sans-serif; font-size: 1.3rem; color: var(--red); }
  .notice h3 { margin: 0 0 0.2rem; font-size: 1.1rem; }
  .notice p { margin: 0; color: var(--steel-dark); }

  /* ===== 일정 ===== */
  .table-wrap { overflow-x: auto; }
  table { width: 100%; border-collapse: collapse; min-width: 420px; }
  th, td { text-align: left; padding: 0.9rem 1rem; border-bottom: 2px solid var(--steel); }
  th { background: var(--ink); color: #fff; font-weight: 600; }
  tr:hover td { background: var(--steel-light); }

  /* ===== 멤버 ===== */
  .members { display: grid; grid-template-columns: repeat(auto-fit, minmax(220px, 1fr)); gap: 2rem; }
  .member { text-align: center; }
  .spoon {
    width: 120px; height: 120px; margin: 0 auto 1rem; border-radius: 50%;
    display: grid; place-content: center;
    background: radial-gradient(circle at 35% 30%, #fff, var(--steel) 60%, var(--steel-dark));
    font-family: "Black Han Sans", sans-serif; font-size: 2.4rem; color: var(--ink);
  }
  .member h3 { margin: 0; font-size: 1.2rem; }
  .member .role { color: var(--red); font-weight: 600; margin: 0.2rem 0 0.5rem; }
  .member p { margin: 0; color: var(--steel-dark); }

  footer { text-align: center; padding: 3rem 1rem; color: var(--steel-dark); font-size: 0.9rem; }

  @media (max-width: 760px) {
    .hero { grid-template-columns: 1fr; }
    .notice { grid-template-columns: 1fr; gap: 0.3rem; }
  }
  @media (prefers-reduced-motion: reduce) {
    .view { animation: none; }
    .bowl::before { transition: none; }
  }
</style>
</head>
<body>

<header>
  <button class="logo" data-tab="home">TEAM JTB</button>
  <nav aria-label="메인 메뉴">
    <button data-tab="home">홈</button>
    <button data-tab="notice">공지</button>
    <button data-tab="schedule">일정</button>
    <button data-tab="members">멤버</button>
  </nav>
</header>

<main>

  <!-- ===== 홈 ===== -->
  <section class="view" id="home">
    <div class="hero">
      <button class="bowl" id="bowl" aria-label="양푼 휘젓기">
        <span class="bowl-title">TEAM<br>JTB<small>눌러서 휘젓기</small></span>
      </button>
      <div class="intro">
        <p class="slogan">One vessel. No rules.<br>Pure chaos, perfectly balanced.</p>
        <p>They said mixology was an art reserved for the refined. We said: hand us the biggest bowl you've got.</p>
        <p>TEAM JTB was born not in a boardroom, but around a single steel basin, where vodka meets whatever else is left standing and hesitation has no seat at the table. We don't measure. We don't garnish. We don't apologize.</p>
        <p>This is not a cocktail hour. This is a ritual: three souls, one 양푼, and an unshakable belief that if it can be poured, it can be combined.</p>
        <ul class="code-list">
          <li>Judgment is optional</li>
          <li>Tolerance is the only stat that matters</li>
          <li>Balance is for people who measure</li>
        </ul>
        <p>We don't sip. We don't savor. We commit to the bowl, to each other, and to whatever tomorrow morning has in store for us.</p>
        <p class="signoff">Bring a spoon.</p>
      </div>
    </div>
  </section>

  <!-- ===== 공지: <article> 묶음을 복사해서 공지를 추가하세요 ===== -->
  <section class="view" id="notice" hidden>
    <h2>공지</h2>
    <article class="notice">
      <time>9/30</time>
      <div>
        <h3>정기모임</h3>
        <p>오후 6시 · 장소 입력</p>
      </div>
    </article>
    <article class="notice">
      <time>10/5</time>
      <div>
        <h3>공지 제목</h3>
        <p>세부 내용을 여기에 적어주세요.</p>
      </div>
    </article>
  </section>

  <!-- ===== 일정: <tr> 줄을 복사해서 일정을 추가하세요 ===== -->
  <section class="view" id="schedule" hidden>
    <h2>일정</h2>
    <div class="table-wrap">
      <table>
        <thead><tr><th>날짜</th><th>내용</th><th>장소</th></tr></thead>
        <tbody>
          <tr><td>10/7</td><td>내용 입력</td><td>장소 입력</td></tr>
          <tr><td>10/14</td><td>내용 입력</td><td>장소 입력</td></tr>
        </tbody>
      </table>
    </div>
  </section>

  <!-- ===== 멤버: 이름·역할·한 줄 소개를 바꿔주세요 ===== -->
  <section class="view" id="members" hidden>
    <h2>멤버</h2>
    <div class="members">
      <div class="member">
        <div class="spoon">J</div>
        <h3>멤버 이름</h3>
        <p class="role">역할</p>
        <p>한 줄 소개</p>
      </div>
      <div class="member">
        <div class="spoon">T</div>
        <h3>멤버 이름</h3>
        <p class="role">역할</p>
        <p>한 줄 소개</p>
      </div>
      <div class="member">
        <div class="spoon">B</div>
        <h3>멤버 이름</h3>
        <p class="role">역할</p>
        <p>한 줄 소개</p>
      </div>
    </div>
  </section>

</main>

<footer>© TEAM JTB</footer>

<script>
  // 버튼을 누르면 해당 화면만 보여주는 코드
  const views = document.querySelectorAll(".view");
  const navButtons = document.querySelectorAll("nav button");

  function showView(id) {
    if (!document.getElementById(id)) id = "home";
    views.forEach(v => v.hidden = (v.id !== id));
    navButtons.forEach(b => {
      if (b.dataset.tab === id) b.setAttribute("aria-current", "page");
      else b.removeAttribute("aria-current");
    });
    window.scrollTo(0, 0);
  }

  document.querySelectorAll("[data-tab]").forEach(btn => {
    btn.addEventListener("click", () => { location.hash = btn.dataset.tab; });
  });

  // 주소 끝의 #notice 같은 부분을 읽어서 화면 전환 (뒤로가기도 작동)
  window.addEventListener("hashchange", () => showView(location.hash.slice(1)));
  showView(location.hash.slice(1) || "home");

  // 양푼 휘젓기
  const bowl = document.getElementById("bowl");
  bowl.addEventListener("click", () => bowl.classList.toggle("stirred"));
</script>
</body>
</html>
</body>
</html>
