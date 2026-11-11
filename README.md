<!doctype html>
<html lang="ko">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>우리 교실 바이브 코딩 보관함</title>
<style>
:root {
  --ink: #253c36;
  --green: #276b54;
  --paper: #faf9f5;
  --line: #dedfd6;
}
* { box-sizing: border-box; }
body {
  margin: 0;
  background: var(--paper);
  color: var(--ink);
  font-family: Arial, 'Malgun Gothic', sans-serif;
  line-height: 1.65;
}
header, main, footer {
  max-width: 1140px;
  margin: auto;
  padding: 24px;
}
nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-bottom: 1px solid var(--line);
  padding-bottom: 20px;
}
.brand { font-weight: 800; }
nav span { font-size: 13px; color: #607067; }
.hero { padding: 66px 0 42px; max-width: 780px; }
.eyebrow {
  color: var(--green);
  font-size: 12px;
  letter-spacing: 2px;
  font-weight: 800;
}
h1 {
  font-size: clamp(32px, 5vw, 54px);
  line-height: 1.25;
  letter-spacing: -2px;
  margin: 16px 0;
}
p { color: #5c6b63; }
.hero p { font-size: 17px; }
.tools {
  display: flex;
  justify-content: space-between;
  gap: 18px;
  align-items: center;
  flex-wrap: wrap;
  margin-bottom: 28px;
}
.filters { display: flex; gap: 8px; flex-wrap: wrap; }
button, input { font: inherit; }
button { cursor: pointer; }
.filter {
  border: 1px solid var(--line);
  border-radius: 24px;
  padding: 8px 19px;
  background: white;
  color: var(--ink);
}
.filter[aria-pressed="true"] {
  background: var(--green);
  color: white;
  border-color: var(--green);
}
input {
  padding: 11px 16px;
  border: 1px solid var(--line);
  border-radius: 12px;
  background: white;
  max-width: 100%;
}
input:focus-visible,
button:focus-visible,
a:focus-visible {
  outline: 3px solid #d69d45;
  outline-offset: 4px;
}
.grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 24px;
}
.card {
  border: 1px solid var(--line);
  background: white;
  border-radius: 19px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  transition: transform .2s, box-shadow .2s;
}
.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 28px #253c3610;
}
.thumb {
  display: block;
  width: 100%;
  aspect-ratio: 16 / 10;
  object-fit: cover;
}
.content {
  padding: 23px;
  display: flex;
  flex-direction: column;
  flex: 1;
}
.tag {
  align-self: flex-start;
  color: var(--green);
  font-size: 12px;
  background: #edf4ee;
  padding: 3px 10px;
  border-radius: 6px;
}
h2 { font-size: 21px; margin: 13px 0 5px; }
.description { font-size: 14px; margin: 0 0 23px; flex: 1; }
.links { display: flex; gap: 8px; flex-wrap: wrap; }
.link {
  background: var(--green);
  color: white;
  text-decoration: none;
  border-radius: 9px;
  padding: 9px 14px;
  font-size: 13px;
  font-weight: 700;
}
.link.secondary { background: #f0f3ee; color: var(--green); }
.pending {
  font-size: 13px;
  color: #788078;
  background: #f3f3ef;
  border-radius: 9px;
  padding: 9px 14px;
}
.count { font-size: 13px; margin-bottom: 18px; }
.empty { padding: 40px; text-align: center; grid-column: 1 / -1; }
footer {
  margin-top: 55px;
  border-top: 1px solid var(--line);
  font-size: 12px;
  color: #707a72;
  padding-bottom: 35px;
}
.note { font-size: 12px; margin-top: 25px; }

@media (max-width: 900px) {
  .grid { grid-template-columns: repeat(2, minmax(0, 1fr)); }
}
@media (max-width: 580px) {
  header, main, footer { padding: 20px; }
  .grid { grid-template-columns: 1fr; }
  .hero { padding: 40px 0 20px; }
  nav span { display: none; }
  input { width: 100%; }
  .tools { align-items: stretch; }
}
@media (prefers-reduced-motion: reduce) {
  .card { transition: none; }
  .card:hover { transform: none; }
}
</style>
</head>
<body>
<header>
  <nav>
    <div class="brand">✳ 교실 속 작은 실험실</div>
    <span>VIBE CODING COLLECTION</span>
  </nav>

  <section class="hero">
    <div class="eyebrow">MAKE · PLAY · LEARN</div>
    <h1>아이디어가 자라는<br>바이브 코딩 보관함</h1>
    <p>
      우리 교실에 필요한 것을 직접 만들어요.<br>
      배움과 놀이를 연결하는 프로젝트들을 한곳에 모았습니다.
    </p>
  </section>
</header>

<main>
  <div class="tools">
    <div class="filters" role="group" aria-label="프로젝트 분류"></div>
    <label>
      <span class="eyebrow">검색 </span>
      <input id="search" type="search"
        placeholder="프로젝트 찾아보기" aria-label="프로젝트 검색">
    </label>
  </div>

  <div class="count" aria-live="polite" id="count"></div>
  <div class="grid" id="grid"></div>
  <p class="note">
    등록된 프로젝트는 서비스 열기 버튼을 눌러 이용하세요.
    나머지 카드는 구성 예시입니다.
  </p>
</main>

<footer>
  작은 아이디어에서 시작하는 즐거운 배움 · 나의 바이브 코딩 포트폴리오
</footer>

<script>
/*
  title: 제목
  description: 설명
  category: 분류
  image: 썸네일 이미지 주소. 비워두면 내장 이미지 사용
  serviceUrl: 실제 웹앱 주소
  padletUrl: 패들렛 주소

  프로젝트를 추가하려면 아래 객체 하나를 복사해 추가하세요.
*/
const projects = [
  {
    title: '2학년 연산복습(덧셈, 뺄셈, 구구단, 시계)',
    description: '덧셈, 뺄셈, 구구단과 시계 읽기를 한곳에서 복습해요.',
    category: '수학',
    symbol: '＋ − × ◷',
    color: '#dceee6',
    image: '',
    serviceUrl: 'https://songjeong-math-magic.edut1841.chatgpt.site/',
    padletUrl: ''
  },
  {
    title: '덧셈 교실',
    description: '수를 더하며 덧셈 실력을 키우는 즐거운 연습 공간.',
    category: '수학',
    symbol: '＋',
    color: '#efe4fb',
    image: '',
    serviceUrl: 'https://happynewyear2026-hj.my.canva.site/23plus',
    padletUrl: ''
  },
  {
    title: '뺄셈 교실',
    description: '수를 빼며 뺄셈 실력을 키우는 즐거운 연습 공간.',
    category: '수학',
    symbol: '−',
    color: '#fce8ca',
    image: '',
    serviceUrl: 'https://sites.google.com/sjes.es.kr/teddy-bear-subtraction-math-ap?usp=sharing',
    padletUrl: ''
  },
  {
    title: '몽키와 구구단 연습',
    description: '몽키와 함께 2단부터 9단까지 즐겁게 곱셈구구를 연습해요.',
    category: '수학',
    symbol: '🐵',
    color: '#e3edcf',
    image: '',
    serviceUrl: 'https://happy-gugudan-garden-k26.roundanole.chatgpt.site/',
    padletUrl: ''
  },
  {
    title: '붕어빵 시계읽기',
    description: '시곗바늘을 살펴보고 몇 시 몇 분인지 알아보아요.',
    category: '수학',
    symbol: '◷',
    color: '#fce8ca',
    image: '',
    serviceUrl: 'https://warm-bungeoppang-clock.workspace-489790.chatgpt.site/',
    padletUrl: ''
  },
  {
    title: '알쏭달쏭 우리말',
    description: '헷갈리는 우리말을 살펴보며 바른 표현을 익혀요.',
    category: '국어',
    symbol: '가 나 다',
    color: '#dfeef4',
    image: '',
    serviceUrl: '',
    padletUrl: ''
  },
  {
    title: '나만의 발명품',
    description: '누군가를 돕는 특별한 발명품을 상상하고 소개해요.',
    category: '창의 활동',
    symbol: '✧',
    color: '#fae0dc',
    image: '',
    serviceUrl: '',
    padletUrl: ''
  },
  {
    title: '우리 반 이야기 모음',
    description: '친구들의 생각과 작품을 패들렛에서 함께 나누어요.',
    category: '창의 활동',
    symbol: '✎',
    color: '#e6e4f6',
    image: '',
    serviceUrl: '',
    padletUrl: ''
  }
];

let selected = '전체';
const grid = document.querySelector('#grid');
const search = document.querySelector('#search');

function validUrl(value) {
  try {
    const u = new URL(value);
    return ['https:', 'http:'].includes(u.protocol) ? u.href : null;
  } catch {
    return null;
  }
}

function thumbnail(p) {
  const svg = `
    <svg xmlns="http://www.w3.org/2000/svg"
      width="640" height="400" viewBox="0 0 640 400">
      <rect width="640" height="400" fill="${p.color}"/>
      <circle cx="530" cy="60" r="120" fill="white" opacity=".3"/>
      <circle cx="80" cy="370" r="140" fill="white" opacity=".25"/>
      <rect x="168" y="78" width="304" height="244"
        rx="32" fill="white" opacity=".65"/>
      <text x="320" y="232" text-anchor="middle"
        font-family="sans-serif" font-size="70"
        font-weight="bold" fill="#36594b">${p.symbol}</text>
    </svg>`;
  return 'data:image/svg+xml;charset=utf-8,' + encodeURIComponent(svg);
}

function render() {
  grid.replaceChildren();

  const shown = projects.filter(p =>
    (selected === '전체' || p.category === selected) &&
    `${p.title} ${p.description} ${p.category}`
      .includes(search.value.trim())
  );

  document.querySelector('#count').textContent =
    `${shown.length}개의 프로젝트 · 구성 예시`;

  if (!shown.length) {
    const e = document.createElement('p');
    e.className = 'empty';
    e.textContent = '검색 결과가 없어요. 다른 단어로 찾아보세요.';
    grid.append(e);
  }

  shown.forEach(p => {
    const card = document.createElement('article');
    card.className = 'card';

    const img = document.createElement('img');
    img.className = 'thumb';
    img.alt = p.title + ' 썸네일';
    img.loading = 'lazy';
    img.src = validUrl(p.image) || thumbnail(p);
    img.onerror = () => {
      img.onerror = null;
      img.src = thumbnail(p);
    };

    const box = document.createElement('div');
    box.className = 'content';

    const tag = document.createElement('span');
    tag.className = 'tag';
    tag.textContent = p.category;

    const title = document.createElement('h2');
    title.textContent = p.title;

    const desc = document.createElement('p');
    desc.className = 'description';
    desc.textContent = p.description;

    const links = document.createElement('div');
    links.className = 'links';

    [
      [p.serviceUrl, '서비스 열기 ↗', false],
      [p.padletUrl, '패들렛 ↗', true]
    ].forEach(([url, label, secondary]) => {
      const href = validUrl(url);
      if (!href) return;

      const a = document.createElement('a');
      a.href = href;
      a.target = '_blank';
      a.rel = 'noopener noreferrer';
      a.className = 'link' + (secondary ? ' secondary' : '');
      a.textContent = label;
      a.setAttribute('aria-label', p.title + ' ' + label + ' (새 창)');
      links.append(a);
    });

    if (!links.childElementCount) {
      const pending = document.createElement('span');
      pending.className = 'pending';
      pending.textContent = '링크 등록 예정';
      links.append(pending);
    }

    box.append(tag, title, desc, links);
    card.append(img, box);
    grid.append(card);
  });
}

const filters = document.querySelector('.filters');

['전체', ...new Set(projects.map(p => p.category))].forEach(category => {
  const b = document.createElement('button');
  b.type = 'button';
  b.className = 'filter';
  b.textContent = category;
  b.setAttribute('aria-pressed', category === selected);

  b.addEventListener('click', () => {
    selected = category;
    for (const el of filters.children) {
      el.setAttribute('aria-pressed', el === b);
    }
    render();
  });

  filters.append(b);
});

search.addEventListener('input', render);
render();
</script>
</body>
</html>
