
<html lang="de">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width,initial-scale=1">
<title>Company Abgaben – Narco City RP</title>
<style>
:root{--bg:#0a0b0f;--panel:#111318;--panel2:#171920;--line:#292d36;--text:#f4f4f5;--muted:#9297a3;--accent:#c9a227;--green:#27c98a;--red:#ef5350;--yellow:#e8b84a}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(circle at top right,#1d1a0c 0,#0a0b0f 38%);color:var(--text);font-family:Inter,Arial,sans-serif}
.app{display:grid;grid-template-columns:245px 1fr;min-height:100vh}.side{border-right:1px solid var(--line);background:#0d0e12;padding:22px 15px;position:sticky;top:0;height:100vh}.brand{font-weight:900;letter-spacing:1px;font-size:20px}.brand small{display:block;color:var(--accent);font-size:10px;letter-spacing:2px;margin-top:4px}.nav{margin-top:30px}.nav button{display:block;width:100%;text-align:left;border:0;background:transparent;color:#b9bdc7;padding:12px 13px;border-radius:9px;margin:4px 0;cursor:pointer}.nav button.active,.nav button:hover{background:#1b1d23;color:#fff}.main{padding:28px;max-width:1500px;width:100%;margin:auto}.top{display:flex;justify-content:space-between;align-items:center;gap:15px;margin-bottom:22px}.top h1{margin:0;font-size:27px}.muted{color:var(--muted);font-size:13px}.cards{display:grid;grid-template-columns:repeat(4,1fr);gap:14px}.card,.panel{background:linear-gradient(180deg,#15171d,#111318);border:1px solid var(--line);border-radius:14px}.card{padding:18px}.card .n{font-size:28px;font-weight:800;margin-top:8px}.green{color:var(--green)}.red{color:var(--red)}.yellow{color:var(--yellow)}.gold{color:var(--accent)}.panel{padding:18px;margin-top:18px}.panel h2{font-size:17px;margin:0 0 14px}.toolbar{display:flex;gap:9px;flex-wrap:wrap;margin-bottom:14px}.toolbar input,.toolbar select{flex:1;min-width:160px}input,select,textarea{background:#0c0e12;border:1px solid #343944;color:#fff;border-radius:8px;padding:10px 11px;outline:none}textarea{min-height:75px;resize:vertical}button.primary{background:var(--accent);color:#111;border:0;font-weight:800}button{border:1px solid #383d48;background:#191c23;color:#eee;padding:10px 12px;border-radius:8px;cursor:pointer}button:hover{filter:brightness(1.1)}table{width:100%;border-collapse:collapse}th,td{padding:12px 9px;border-bottom:1px solid var(--line);text-align:left;font-size:13px}th{color:#8e94a0;font-size:11px;text-transform:uppercase;letter-spacing:.5px}.badge{display:inline-flex;padding:5px 8px;border-radius:99px;font-size:11px;font-weight:800}.b-green{background:#093b2b;color:#6af0ba}.b-red{background:#45191a;color:#ff8d8a}.b-yellow{background:#45340f;color:#ffd66e}.actions{display:flex;gap:5px}.empty{text-align:center;color:var(--muted);padding:35px}.modal{position:fixed;inset:0;background:#000b;display:none;align-items:center;justify-content:center;padding:20px}.modal.show{display:flex}.box{width:min(520px,100%);background:#15171d;border:1px solid var(--line);border-radius:14px;padding:20px}.formgrid{display:grid;grid-template-columns:1fr 1fr;gap:10px}.formgrid .full{grid-column:1/-1}.box h2{margin-top:0}.footer{color:#686e7b;font-size:11px;margin-top:20px}
@media(max-width:900px){.app{grid-template-columns:1fr}.side{position:relative;height:auto;border-right:0;border-bottom:1px solid var(--line)}.cards{grid-template-columns:1fr 1fr}.main{padding:16px;overflow:auto}}@media(max-width:600px){.cards{grid-template-columns:1fr}.formgrid{grid-template-columns:1fr}.formgrid .full{grid-column:auto}table{min-width:850px}.panel{overflow:auto}}
</style>
</head>
<body>
<div class="app">
<aside class="side">
 <div class="brand">COMPANY ABGABEN<small>NARCO CITY • ROLEPLAY</small></div>
 <div class="nav">
  <button class="active" onclick="showTab('dashboard',this)">▣ Dashboard</button>
  <button onclick="showTab('abgaben',this)">◷ Wochenabgaben</button>
  <button onclick="showTab('spieler',this)">♙ Mitarbeiter</button>
  <button onclick="showTab('historie',this)">▤ Historie</button>
 </div>
 <div class="footer">Lokale Demo-Version • Daten werden im Browser gespeichert</div>
</aside>
<main class="main">
<section id="dashboard">
 <div class="top"><div><h1>Wochenabgaben</h1><div class="muted" id="dashWeek"></div></div><button class="primary" onclick="openAdd()">+ Mitarbeiter / Abgabe</button></div>
 <div class="cards">
  <div class="card"><div class="muted">Gesamt</div><div class="n" id="cTotal">0</div></div>
  <div class="card"><div class="muted green">Metall abgegeben</div><div class="n green" id="cDone">0</div></div>
  <div class="card"><div class="muted red">Nicht abgegeben</div><div class="n red" id="cMissing">0</div></div>
  <div class="card"><div class="muted yellow">Freigestellt</div><div class="n yellow" id="cFree">0</div></div>
 </div>
 <div class="panel"><h2>Aktuelle Woche – Übersicht</h2><div id="dashboardTable"></div></div>
</section>

<section id="abgaben" style="display:none">
 <div class="top"><div><h1>Wochenabgaben</h1><div class="muted">Abgabestatus pro Kalenderwoche verwalten</div></div><button class="primary" onclick="openAdd()">+ Eintrag</button></div>
 <div class="panel">
  <div class="toolbar"><select id="weekSel" onchange="renderAll()"></select><select id="statusSel" onchange="renderAll()"><option value="">Alle Status</option><option value="done">Metall abgegeben</option><option value="missing">Nicht abgegeben</option><option value="free">Freigestellt</option></select><input id="q" oninput="renderAll()" placeholder="Mitarbeiter suchen…"></div>
  <div id="mainTable"></div>
 </div>
</section>

<section id="spieler" style="display:none">
 <div class="top"><div><h1>Mitarbeiter</h1><div class="muted">Mitarbeiter, die in der Abgabenliste geführt werden</div></div><button class="primary" onclick="openPlayer()">+ Mitarbeiter</button></div>
 <div class="panel"><div id="playersTable"></div></div>
</section>

<section id="historie" style="display:none">
 <div class="top"><div><h1>Historie</h1><div class="muted">Vergangene Wochen auf einen Blick</div></div></div>
 <div class="panel"><div id="historyTable"></div></div>
</section>
</main></div>

<div class="modal" id="modal"><div class="box" id="modalBox"></div></div>

<script>
const KEY='narco_city_abgaben_v1';
let db=JSON.parse(localStorage.getItem(KEY)||'{"players":[],"entries":[]}');
const week=()=>{let d=new Date(),t=new Date(Date.UTC(d.getFullYear(),d.getMonth(),d.getDate()));let day=t.getUTCDay()||7;t.setUTCDate(t.getUTCDate()+4-day);let ys=new Date(Date.UTC(t.getUTCFullYear(),0,1));let w=Math.ceil((((t-ys)/86400000)+1)/7);return t.getUTCFullYear()+'-KW'+String(w).padStart(2,'0')};
function save(){localStorage.setItem(KEY,JSON.stringify(db))}
function esc(s){return String(s??'').replace(/[&<>"']/g,c=>({'&':'&amp;','<':'&lt;','>':'&gt;','"':'&quot;',"'":'&#039;'}[c]))}
function statusLabel(s){return s==='done'?'<span class="badge b-green">Metall abgegeben</span>':s==='missing'?'<span class="badge b-red">Nicht abgegeben</span>':'<span class="badge b-yellow">Freigestellt</span>'}
function showTab(id,btn){document.querySelectorAll('main section').forEach(x=>x.style.display='none');document.getElementById(id).style.display='block';document.querySelectorAll('.nav button').forEach(x=>x.classList.remove('active'));btn.classList.add('active');renderAll()}
function refreshWeekSelect(){let ws=[week(),...db.entries.map(e=>e.week)].filter((x,i,a)=>a.indexOf(x)===i).sort().reverse();let s=document.getElementById('weekSel'),old=s.value||week();s.innerHTML=ws.map(w=>`<option>${w}</option>`).join('');s.value=ws.includes(old)?old:week()}
function openAdd(id=null){
 let e=id?db.entries.find(x=>x.id===id):null;
 document.getElementById('modalBox').innerHTML=`<h2>${e?'Abgabe bearbeiten':'Neue Wochenabgabe'}</h2>
 <div class="formgrid">
 <input id="mName" placeholder="Mitarbeitername" value="${esc(e?.name||'')}">
 <input id="mId" placeholder="Charakter-ID (optional)" value="${esc(e?.charId||'')}">
 <select id="mStatus"><option value="done">Metall abgegeben</option><option value="missing">Nicht abgegeben</option><option value="free">Freigestellt</option></select>
 <input id="mWeek" placeholder="Woche" value="${esc(e?.week||week())}">
 <input id="mAmount" type="number" min="0" step="1" placeholder="Menge Metall (optional)" value="${e?.amount??''}">
 <input id="mBy" placeholder="Bearbeitet von" value="${esc(e?.by||'')}">
 <textarea class="full" id="mNote" placeholder="Notiz">${esc(e?.note||'')}</textarea>
 <div class="full" style="display:flex;gap:8px;justify-content:flex-end"><button onclick="closeModal()">Abbrechen</button><button class="primary" onclick="saveEntry(${id||0})">Speichern</button></div></div>`;
 document.getElementById('mStatus').value=e?.status||'done';document.getElementById('modal').classList.add('show')
}
function saveEntry(id){
 let name=document.getElementById('mName').value.trim();if(!name)return alert('Bitte Mitarbeitername eingeben.');
 let obj={id:id||Date.now(),name,charId:document.getElementById('mId').value.trim(),status:document.getElementById('mStatus').value,week:document.getElementById('mWeek').value.trim()||week(),amount:Number(document.getElementById('mAmount').value)||0,by:document.getElementById('mBy').value.trim(),note:document.getElementById('mNote').value.trim(),updated:new Date().toLocaleString('de-AT')};
 if(id){let i=db.entries.findIndex(x=>x.id===id);db.entries[i]=obj}else db.entries.push(obj);
 if(!db.players.some(p=>p.name.toLowerCase()===name.toLowerCase()))db.players.push({id:Date.now()+1,name,charId:obj.charId});
 save();closeModal();refreshWeekSelect();renderAll()
}
function openPlayer(){
 document.getElementById('modalBox').innerHTML=`<h2>Mitarbeiter hinzufügen</h2><div class="formgrid"><input id="pName" placeholder="Mitarbeitername"><input id="pId" placeholder="Charakter-ID (optional)"><div class="full" style="display:flex;gap:8px;justify-content:flex-end"><button onclick="closeModal()">Abbrechen</button><button class="primary" onclick="savePlayer()">Speichern</button></div></div>`;
 document.getElementById('modal').classList.add('show')
}
function savePlayer(){let n=document.getElementById('pName').value.trim();if(!n)return;if(db.players.some(p=>p.name.toLowerCase()===n.toLowerCase()))return alert('Mitarbeiter existiert bereits.');db.players.push({id:Date.now(),name:n,charId:document.getElementById('pId').value.trim()});save();closeModal();renderAll()}
function closeModal(){document.getElementById('modal').classList.remove('show')}
function delEntry(id){if(confirm('Eintrag wirklich löschen?')){db.entries=db.entries.filter(e=>e.id!==id);save();renderAll()}}
function delPlayer(id){if(confirm('Mitarbeiter löschen? Bestehende Abgaben bleiben erhalten.')){db.players=db.players.filter(p=>p.id!==id);save();renderAll()}}
function rows(list){if(!list.length)return '<div class="empty">Keine Einträge vorhanden.</div>';return `<table><thead><tr><th>Mitarbeiter</th><th>Char-ID</th><th>Status</th><th>Metall</th><th>Notiz</th><th>Bearbeitet von</th><th>Aktionen</th></tr></thead><tbody>${list.map(e=>`<tr><td><b>${esc(e.name)}</b></td><td>${esc(e.charId||'–')}</td><td>${statusLabel(e.status)}</td><td>${e.amount?esc(e.amount)+' kg':'–'}</td><td>${esc(e.note||'–')}</td><td>${esc(e.by||'–')}</td><td><div class="actions"><button onclick="openAdd(${e.id})">Bearbeiten</button><button onclick="delEntry(${e.id})">Löschen</button></div></td></tr>`).join('')}</tbody></table>`}
function renderAll(){
 refreshWeekSelect();let w=document.getElementById('weekSel').value||week();let sf=document.getElementById('statusSel').value;let q=(document.getElementById('q').value||'').toLowerCase();
 let list=db.entries.filter(e=>e.week===w&&(!sf||e.status===sf)&&e.name.toLowerCase().includes(q));
 let cur=db.entries.filter(e=>e.week===week());
 document.getElementById('dashWeek').textContent='Aktuelle Woche: '+week();
 document.getElementById('cTotal').textContent=cur.length;document.getElementById('cDone').textContent=cur.filter(e=>e.status==='done').length;document.getElementById('cMissing').textContent=cur.filter(e=>e.status==='missing').length;document.getElementById('cFree').textContent=cur.filter(e=>e.status==='free').length;
 document.getElementById('mainTable').innerHTML=rows(list);document.getElementById('dashboardTable').innerHTML=rows(cur);
 document.getElementById('playersTable').innerHTML=db.players.length?`<table><thead><tr><th>Mitarbeiter</th><th>Char-ID</th><th>Aktueller Status</th><th>Aktion</th></tr></thead><tbody>${db.players.map(p=>{let e=db.entries.find(x=>x.week===week()&&x.name.toLowerCase()===p.name.toLowerCase());return `<tr><td><b>${esc(p.name)}</b></td><td>${esc(p.charId||'–')}</td><td>${e?statusLabel(e.status):'<span class="badge b-red">Kein Eintrag</span>'}</td><td><div class="actions"><button onclick="openAdd()">Abgabe erfassen</button><button onclick="delPlayer(${p.id})">Entfernen</button></div></td></tr>`}).join('')}</tbody></table>`:'<div class="empty">Noch keine Mitarbeiter angelegt.</div>';
 let weeks=[...new Set(db.entries.map(e=>e.week))].sort().reverse();
 document.getElementById('historyTable').innerHTML=weeks.length?`<table><thead><tr><th>Woche</th><th>Gesamt</th><th>Abgegeben</th><th>Nicht abgegeben</th><th>Freigestellt</th></tr></thead><tbody>${weeks.map(x=>{let a=db.entries.filter(e=>e.week===x);return `<tr><td><b>${x}</b></td><td>${a.length}</td><td class="green">${a.filter(e=>e.status==='done').length}</td><td class="red">${a.filter(e=>e.status==='missing').length}</td><td class="yellow">${a.filter(e=>e.status==='free').length}</td></tr>`}).join('')}</tbody></table>`:'<div class="empty">Noch keine Historie.</div>';
}
document.getElementById('modal').addEventListener('click',e=>{if(e.target.id==='modal')closeModal()});
renderAll();
</script>
</body></html>
