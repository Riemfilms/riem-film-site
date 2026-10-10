# riem-film-site
RIEM FILM - Independent Cinema &amp; Stories Website
from pathlib import Path

html = r'''<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>RIEM FILM | Cinema & Stories</title>
<style>
:root{--bg:#090909;--panel:#151515;--gold:#d8b56d;--text:#f5f2eb;--muted:#aaa}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;background:var(--bg);color:var(--text);font-family:Arial,Helvetica,sans-serif}
header{position:sticky;top:0;z-index:10;background:rgba(8,8,8,.94);backdrop-filter:blur(10px);border-bottom:1px solid #28231a}
.nav{max-width:1160px;margin:auto;padding:16px 22px;display:flex;align-items:center;justify-content:space-between;gap:16px}
.brand{font-size:22px;letter-spacing:3px;font-weight:800;color:var(--gold)}.brand small{display:block;font-size:9px;letter-spacing:4px;color:#ddd;margin-top:4px}
nav{display:flex;gap:18px;align-items:center;flex-wrap:wrap}a{color:var(--text);text-decoration:none}nav a:hover{color:var(--gold)}
button,.button{border:1px solid var(--gold);background:var(--gold);color:#111;font-weight:700;padding:10px 15px;border-radius:4px;cursor:pointer}
button.secondary{background:transparent;color:var(--gold)}button.danger{background:#742b2b;color:#fff;border-color:#742b2b}
.hero{min-height:470px;display:flex;align-items:center;background:linear-gradient(90deg,#090909 0%,rgba(9,9,9,.92) 36%,rgba(9,9,9,.35) 100%),url('https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=1800&q=85') center/cover}
.hero-inner{max-width:1160px;width:100%;margin:auto;padding:70px 22px}.eyebrow{color:var(--gold);letter-spacing:4px;font-size:12px}.hero h1{font-size:clamp(36px,6vw,66px);max-width:650px;line-height:1.04;margin:16px 0}.hero p{max-width:560px;color:#d0d0d0;line-height:1.7}
section{max-width:1160px;margin:auto;padding:42px 22px}.section-head{display:flex;align-items:end;justify-content:space-between;gap:15px;margin-bottom:22px}.section-head h2{margin:0;font-size:26px}.section-head p{color:var(--muted);margin:7px 0 0}
.grid{display:grid;grid-template-columns:repeat(4,minmax(0,1fr));gap:18px}.movie{background:var(--panel);border:1px solid #282828;border-radius:7px;overflow:hidden;transition:.2s}.movie:hover{transform:translateY(-4px);border-color:#8d7446}.poster{width:100%;aspect-ratio:2/3;object-fit:cover;background:#222;display:block}.movie-info{padding:14px}.movie h3{margin:0 0 8px;font-size:17px}.meta{color:var(--gold);font-size:12px;margin-bottom:8px}.movie p{color:#bbb;font-size:13px;line-height:1.5;min-height:40px}.movie-actions{display:flex;gap:8px;flex-wrap:wrap}.movie-actions button{padding:8px 10px;font-size:12px}
.about{background:#111;border-top:1px solid #29231a;border-bottom:1px solid #29231a;max-width:none}.about-inner{max-width:1160px;margin:auto;padding:45px 22px;display:grid;grid-template-columns:1.2fr 1fr;gap:35px;align-items:center}.about h2{font-size:30px;margin-top:0}.about p{color:#bbb;line-height:1.8}.quote{border-left:3px solid var(--gold);padding:20px;color:#ddd;font-size:19px;line-height:1.6}
footer{padding:28px 22px;text-align:center;color:#777;font-size:13px;border-top:1px solid #222}.admin-overlay{display:none;position:fixed;inset:0;z-index:30;background:rgba(0,0,0,.78);overflow:auto;padding:20px}.admin{max-width:900px;margin:20px auto;background:#111;border:1px solid #5a4a2b;border-radius:8px;padding:22px}.admin-top{display:flex;justify-content:space-between;gap:12px;align-items:center}.admin h2{margin-top:0;color:var(--gold)}.form-grid{display:grid;grid-template-columns:1fr 1fr;gap:14px}.field{display:flex;flex-direction:column;gap:7px}.field.full{grid-column:1/-1}.field label{font-size:13px;color:#ccc}.field input,.field textarea,.field select{width:100%;background:#202020;border:1px solid #444;color:white;padding:11px;border-radius:4px;font:inherit}.field textarea{min-height:85px;resize:vertical}.form-actions{display:flex;gap:10px;flex-wrap:wrap;margin-top:16px}.admin-list{margin-top:25px;border-top:1px solid #333;padding-top:18px}.admin-item{display:flex;justify-content:space-between;align-items:center;gap:12px;padding:12px 0;border-bottom:1px solid #292929}.admin-item span{color:#ddd}.small{font-size:12px;color:#888;line-height:1.6}.empty{padding:35px;text-align:center;color:#888;border:1px dashed #444;border-radius:7px;grid-column:1/-1}
.modal{display:none;position:fixed;inset:0;background:rgba(0,0,0,.88);z-index:40;align-items:center;justify-content:center;padding:20px}.modal-card{width:min(900px,100%);background:#111;border:1px solid #4b3d24;padding:18px;border-radius:8px}.modal-card video,.modal-card iframe{width:100%;aspect-ratio:16/9;background:#000;border:0}.modal-card h2{color:var(--gold)}
@media(max-width:850px){.grid{grid-template-columns:repeat(2,minmax(0,1fr))}.about-inner{grid-template-columns:1fr}.hero{min-height:400px}}
@media(max-width:520px){.nav{align-items:flex-start;flex-direction:column}.grid{gap:10px}.movie-info{padding:10px}.movie h3{font-size:15px}.movie p{font-size:12px}.hero-inner{padding-top:48px;padding-bottom:48px}.form-grid{grid-template-columns:1fr}.field.full{grid-column:auto}.admin{padding:15px}.section-head h2{font-size:22px}}
</style>
</head>
<body>
<header><div class="nav">
  <a href="#" class="brand" id="brand">RIEM FILM<small>RESPECT · INNOVATION · ENERGY · MISSION</small></a>
  <nav><a href="#home">Trang chủ</a><a href="#movies">Kho phim</a><a href="#about">Về chúng tôi</a><button class="secondary" onclick="openAdmin()">Quản trị</button></nav>
</div></header>
<main>
<section class="hero" id="home" style="max-width:none">
  <div class="hero-inner"><div class="eyebrow" id="heroEyebrow">INDEPENDENT FILM PRODUCTION</div><h1 id="heroTitle">Mỗi khung hình,<br>một câu chuyện.</h1><p id="heroText">Nơi những câu chuyện đời thường được kể bằng cảm xúc, ánh sáng và những khoảnh khắc chân thật.</p><a class="button" href="#movies">Khám phá phim</a></div>
</section>
<section id="movies"><div class="section-head"><div><h2 id="movieHeading">Tác phẩm nổi bật</h2><p id="movieSubheading">Những câu chuyện từ RIEM FILM</p></div><span class="eyebrow">OUR FILMS</span></div><div class="grid" id="movieGrid"></div></section>
<div class="about" id="about"><div class="about-inner"><div><div class="eyebrow">ABOUT RIEM FILM</div><h2 id="aboutTitle">Kể chuyện bằng sự chân thành.</h2><p id="aboutText">RIEM FILM hướng đến những tác phẩm gần gũi, giàu cảm xúc và mang dấu ấn riêng. Chúng tôi tin rằng một câu chuyện tốt có thể bắt đầu từ những điều rất bình thường.</p></div><div class="quote" id="aboutQuote">“Tôn trọng câu chuyện. Đổi mới cách kể. Làm việc bằng năng lượng. Theo đuổi sứ mệnh.”</div></div></div>
</main>
<footer><span id="footerText">© 2026 RIEM FILM · Independent stories, lasting emotions.</span><br><span class="small">Bản mẫu website tự quản lý trên trình duyệt. Hãy sao lưu dữ liệu thường xuyên.</span></footer>

<div class="admin-overlay" id="adminOverlay"><div class="admin">
  <div class="admin-top"><div><h2>RIEM FILM · ADMIN PANEL</h2><div class="small">Chỉnh sửa nội dung website và quản lý danh sách phim.</div></div><button class="secondary" onclick="closeAdmin()">Đóng ✕</button></div>
  <div id="loginBox">
    <p>Đăng nhập quản trị để chỉnh sửa website.</p>
    <div class="form-grid"><div class="field"><label>Tên đăng nhập</label><input id="adminUser" value="admin" autocomplete="username"></div><div class="field"><label>Mật khẩu demo</label><input id="adminPass" type="password" placeholder="Nhập mật khẩu" autocomplete="current-password"></div></div>
    <div class="form-actions"><button onclick="login()">Đăng nhập</button></div>
    <p class="small">Mật khẩu mẫu: <b>riem2026</b>. Đây chỉ là khóa giao diện phía trình duyệt, chưa phải hệ thống bảo mật thật khi đưa lên Internet.</p>
  </div>
  <div id="adminContent" style="display:none">
    <h3>Chỉnh sửa giao diện</h3>
    <div class="form-grid">
      <div class="field"><label>Tên thương hiệu</label><input id="cfgBrand"></div><div class="field"><label>Dòng chữ nhỏ dưới logo</label><input id="cfgTagline"></div>
      <div class="field"><label>Tiêu đề banner</label><input id="cfgHeroTitle"></div><div class="field"><label>Dòng nhãn banner</label><input id="cfgHeroEyebrow"></div>
      <div class="field full"><label>Mô tả banner</label><textarea id="cfgHeroText"></textarea></div>
      <div class="field"><label>Tiêu đề khu vực phim</label><input id="cfgMovieHeading"></div><div class="field"><label>Mô tả khu vực phim</label><input id="cfgMovieSub"></div>
      <div class="field"><label>Tiêu đề giới thiệu</label><input id="cfgAboutTitle"></div><div class="field"><label>Câu slogan</label><input id="cfgQuote"></div>
      <div class="field full"><label>Nội dung giới thiệu</label><textarea id="cfgAboutText"></textarea></div>
      <div class="field full"><label>Chân trang</label><input id="cfgFooter"></div>
      <div class="field full"><label>Ảnh nền banner (URL ảnh)</label><input id="cfgHeroImage" placeholder="https://..."></div>
    </div>
    <div class="form-actions"><button onclick="saveSettings()">Lưu giao diện</button><button class="secondary" onclick="exportData()">Sao lưu dữ liệu JSON</button><label class="button" for="importFile" style="display:inline-flex;align-items:center">Nhập dữ liệu JSON</label><input id="importFile" type="file" accept=".json,application/json" style="display:none" onchange="importData(event)"><button class="secondary" onclick="logout()">Đăng xuất</button></div>
    <div class="admin-list"><h3 id="formTitle">Thêm phim mới</h3>
      <input type="hidden" id="editId">
      <div class="form-grid">
        <div class="field"><label>Tên phim *</label><input id="mTitle" placeholder="Ví dụ: Thế Giới Của Anh"></div>
        <div class="field"><label>Thể loại / năm</label><input id="mMeta" placeholder="Tâm lý · 2026"></div>
        <div class="field full"><label>Mô tả phim</label><textarea id="mDesc" placeholder="Giới thiệu ngắn về tác phẩm"></textarea></div>
        <div class="field full"><label>URL ảnh poster</label><input id="mPoster" placeholder="https://.../poster.jpg"></div>
        <div class="field full"><label>URL video / trailer</label><input id="mVideo" placeholder="Link MP4 trực tiếp hoặc link YouTube"></div>
      </div>
      <div class="form-actions"><button onclick="saveMovie()">Lưu phim</button><button class="secondary" onclick="clearMovieForm()">Hủy chỉnh sửa</button></div>
      <div id="adminMovieList"></div>
    </div>
  </div>
</div></div>
<div class="modal" id="playerModal" onclick="if(event.target===this)closePlayer()"><div class="modal-card"><button class="secondary" style="float:right" onclick="closePlayer()">Đóng ✕</button><h2 id="playerTitle"></h2><div id="playerContent"></div><p class="small" id="playerDesc"></p></div></div>

<script>
const KEY='riemFilmSiteData_v1';
const defaultData={
 settings:{brand:'RIEM FILM',tagline:'RESPECT · INNOVATION · ENERGY · MISSION',heroTitle:'Mỗi khung hình,\\nmột câu chuyện.',heroEyebrow:'INDEPENDENT FILM PRODUCTION',heroText:'Nơi những câu chuyện đời thường được kể bằng cảm xúc, ánh sáng và những khoảnh khắc chân thật.',movieHeading:'Tác phẩm nổi bật',movieSub:'Những câu chuyện từ RIEM FILM',aboutTitle:'Kể chuyện bằng sự chân thành.',aboutText:'RIEM FILM hướng đến những tác phẩm gần gũi, giàu cảm xúc và mang dấu ấn riêng. Chúng tôi tin rằng một câu chuyện tốt có thể bắt đầu từ những điều rất bình thường.',quote:'“Tôn trọng câu chuyện. Đổi mới cách kể. Làm việc bằng năng lượng. Theo đuổi sứ mệnh.”',footer:'© 2026 RIEM FILM · Independent stories, lasting emotions.',heroImage:'https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=1800&q=85'},
 movies:[
 {id:'demo1',title:'Thế Giới Của Anh',meta:'Tâm lý · Tình cảm',desc:'Một câu chuyện về sự tự ti, lòng can đảm và cơ hội được yêu thương.',poster:'https://images.unsplash.com/photo-1519608487953-e999c86e7455?auto=format&fit=crop&w=700&q=85',video:''},
 {id:'demo2',title:'Ngày Gió Trở Về',meta:'Tâm lý · Chính kịch',desc:'Đôi khi hành trình trở về cũng là hành trình tìm lại chính mình.',poster:'https://images.unsplash.com/photo-1470252649378-9c29740c9fa8?auto=format&fit=crop&w=700&q=85',video:''},
 {id:'demo3',title:'Phim Trong Phim',meta:'Đời thường · Sáng tạo',desc:'Phía sau mỗi khung hình là một câu chuyện chưa được kể.',poster:'https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=700&q=85',video:''}
 ]};
let data=loadData();let loggedIn=false;
function loadData(){try{const x=JSON.parse(localStorage.getItem(KEY));if(x&&x.settings&&Array.isArray(x.movies))return x}catch(e){}return structuredClone(defaultData)}
function persist(){localStorage.setItem(KEY,JSON.stringify(data))}
function esc(s=''){return String(s).replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#39;'}[c]))}
function render(){const s=data.settings;document.title=s.brand+' | Cinema & Stories';document.getElementById('brand').innerHTML=esc(s.brand)+'<small>'+esc(s.tagline)+'</small>';document.getElementById('heroEyebrow').textContent=s.heroEyebrow;document.getElementById('heroTitle').innerHTML=esc(s.heroTitle).replace(/\\n|\n/g,'<br>');document.getElementById('heroText').textContent=s.heroText;document.getElementById('movieHeading').textContent=s.movieHeading;document.getElementById('movieSubheading').textContent=s.movieSub;document.getElementById('aboutTitle').textContent=s.aboutTitle;document.getElementById('aboutText').textContent=s.aboutText;document.getElementById('aboutQuote').textContent=s.quote;document.getElementById('footerText').textContent=s.footer;document.querySelector('.hero').style.backgroundImage=`linear-gradient(90deg,#090909 0%,rgba(9,9,9,.92) 36%,rgba(9,9,9,.35) 100%),url("${(s.heroImage||'').replace(/["\\]/g,'')}")`;
const grid=document.getElementById('movieGrid');if(!data.movies.length){grid.innerHTML='<div class="empty">Chưa có phim nào. Mở Quản trị để thêm tác phẩm đầu tiên.</div>';return}
grid.innerHTML=data.movies.map(m=>`<article class="movie"><img class="poster" src="${esc(m.poster||'')}" alt="${esc(m.title)} poster" onerror="this.style.visibility='hidden'"><div class="movie-info"><div class="meta">${esc(m.meta||'RIEM FILM')}</div><h3>${esc(m.title)}</h3><p>${esc(m.desc||'')}</p><div class="movie-actions"><button onclick="playMovie('${esc(m.id)}')">Xem phim</button></div></div></article>`).join('')}
function openAdmin(){document.getElementById('adminOverlay').style.display='block';document.body.style.overflow='hidden';if(loggedIn)showAdmin();else{document.getElementById('loginBox').style.display='block';document.getElementById('adminContent').style.display='none'}}
function closeAdmin(){document.getElementById('adminOverlay').style.display='none';document.body.style.overflow=''}
function login(){if(document.getElementById('adminUser').value==='admin'&&document.getElementById('adminPass').value==='riem2026'){loggedIn=true;showAdmin()}else alert('Thông tin đăng nhập chưa đúng.')}
function showAdmin(){document.getElementById('loginBox').style.display='none';document.getElementById('adminContent').style.display='block';fillSettings();renderAdminMovies()}
function logout(){loggedIn=false;document.getElementById('adminPass').value='';document.getElementById('adminContent').style.display='none';document.getElementById('loginBox').style.display='block'}
function fillSettings(){let s=data.settings;let map={cfgBrand:'brand',cfgTagline:'tagline',cfgHeroTitle:'heroTitle',cfgHeroEyebrow:'heroEyebrow',cfgHeroText:'heroText',cfgMovieHeading:'movieHeading',cfgMovieSub:'movieSub',cfgAboutTitle:'aboutTitle',cfgQuote:'quote',cfgAboutText:'aboutText',cfgFooter:'footer',cfgHeroImage:'heroImage'};for(let id in map)document.getElementById(id).value=s[map[id]]||''}
function saveSettings(){let map={cfgBrand:'brand',cfgTagline:'tagline',cfgHeroTitle:'heroTitle',cfgHeroEyebrow:'heroEyebrow',cfgHeroText:'heroText',cfgMovieHeading:'movieHeading',cfgMovieSub:'movieSub',cfgAboutTitle:'aboutTitle',cfgQuote:'quote',cfgAboutText:'aboutText',cfgFooter:'footer',cfgHeroImage:'heroImage'};for(let id in map)data.settings[map[id]]=document.getElementById(id).value;persist();render();alert('Đã lưu giao diện trên trình duyệt này.')}
function clearMovieForm(){['editId','mTitle','mMeta','mDesc','mPoster','mVideo'].forEach(id=>document.getElementById(id).value='');document.getElementById('formTitle').textContent='Thêm phim mới'}
function saveMovie(){let title=document.getElementById('mTitle').value.trim();if(!title){alert('Vui lòng nhập tên phim.');return}let id=document.getElementById('editId').value||('film_'+Date.now());let m={id,title,meta:document.getElementById('mMeta').value.trim(),desc:document.getElementById('mDesc').value.trim(),poster:document.getElementById('mPoster').value.trim(),video:document.getElementById('mVideo').value.trim()};let i=data.movies.findIndex(x=>x.id===id);if(i>=0)data.movies[i]=m;else data.movies.unshift(m);persist();render();renderAdminMovies();clearMovieForm();alert('Đã lưu phim.')}
function editMovie(id){let m=data.movies.find(x=>x.id===id);if(!m)return;document.getElementById('editId').value=m.id;document.getElementById('mTitle').value=m.title;document.getElementById('mMeta').value=m.meta||'';document.getElementById('mDesc').value=m.desc||'';document.getElementById('mPoster').value=m.poster||'';document.getElementById('mVideo').value=m.video||'';document.getElementById('formTitle').textContent='Chỉnh sửa phim: '+m.title;document.getElementById('mTitle').scrollIntoView({behavior:'smooth',block:'center'})}
function deleteMovie(id){let m=data.movies.find(x=>x.id===id);if(m&&confirm('Xóa phim "'+m.title+'"?')){data.movies=data.movies.filter(x=>x.id!==id);persist();render();renderAdminMovies();if(document.getElementById('editId').value===id)clearMovieForm()}}
function renderAdminMovies(){let box=document.getElementById('adminMovieList');if(!data.movies.length){box.innerHTML='<p class="small">Danh sách phim đang trống.</p>';return}box.innerHTML='<h3>Danh sách phim ('+data.movies.length+')</h3>'+data.movies.map(m=>`<div class="admin-item"><span>${esc(m.title)} <small>— ${esc(m.meta||'')}</small></span><div style="display:flex;gap:7px"><button class="secondary" onclick="editMovie('${esc(m.id)}')">Sửa</button><button class="danger" onclick="deleteMovie('${esc(m.id)}')">Xóa</button></div></div>`).join('')}
function playMovie(id){let m=data.movies.find(x=>x.id===id);if(!m)return;if(!m.video){alert('Phim này chưa có link video. Hãy đăng nhập Quản trị và thêm URL video.');return}document.getElementById('playerTitle').textContent=m.title;document.getElementById('playerDesc').textContent=m.desc||'';let url=m.video;let content=document.getElementById('playerContent');if(/youtube\.com|youtu\.be/.test(url)){let match=url.match(/(?:youtu\.be\/|v=|embed\/)([A-Za-z0-9_-]{6,})/);if(match)content.innerHTML='<iframe allowfullscreen src="https://www.youtube.com/embed/'+match[1]+'" title="Video phim"></iframe>';else content.innerHTML='<p>Link YouTube chưa hợp lệ.</p>'}else content.innerHTML='<video controls playsinline src="'+esc(url)+'"></video>';document.getElementById('playerModal').style.display='flex'}
function closePlayer(){document.getElementById('playerModal').style.display='none';document.getElementById('playerContent').innerHTML=''}
function exportData(){let blob=new Blob([JSON.stringify(data,null,2)],{type:'application/json'});let a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download='riem-film-backup.json';a.click();URL.revokeObjectURL(a.href)}
function importData(e){let f=e.target.files[0];if(!f)return;let r=new FileReader();r.onload=()=>{try{let obj=JSON.parse(r.result);if(!obj.settings||!Array.isArray(obj.movies))throw Error();data=obj;persist();render();fillSettings();renderAdminMovies();alert('Đã nhập dữ liệu thành công.')}catch(err){alert('File JSON không đúng định dạng website.')}};r.readAsText(f);e.target.value=''}
render();
</script>
</body>
</html>'''
path = Path("/mnt/data/riem_film_editable.html")
path.write_text(html, encoding="utf-8")
print(f"Đã tạo website HTML: {path} ({path.stat().st_size:,} bytes)")
