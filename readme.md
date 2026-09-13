```
<!DOCTYPE html>
<html lang="zh-CN" data-theme="light">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1,user-scalable=no">
<title>API记账本</title>
<style>*{margin:0;padding:0;box-sizing:border-box}
:root{--t:.25s}
body,html{-webkit-tap-highlight-color:transparent}
.cki,.fab,.ii,.li,.pr,.qi,.ri,.si,.tb,button,summary{-webkit-tap-highlight-color:transparent;user-select:none;-webkit-user-select:none}
[data-theme=light]{--bg:#fff5f5;--c:#fff;--c2:#fff8f8;--bd:#fcd;--tx:#3a2a2a;--t2:#8a6a6a;--t3:#bfa0a0;--ac:#f27ea0;--gn:#5ab87a;--rd:#e06070;--og:#d4903a;--sh:0 2px 8px rgba(200,140,160,.1)}
[data-theme=dark]{--bg:#1F1D33;--c:#161526;--c2:#1F1D33;--bd:#322E47;--tx:#e8e8e8;--t2:#aaa;--t3:#aaa;--ac:#f27ea0;--gn:#6bcf8e;--rd:#e87272;--og:#e8a84c;--sh:0 2px 8px rgba(0,0,0,.2)}
body{font-family:-apple-system,"PingFang SC",sans-serif;background:var(--bg);color:var(--tx);font-size:14px;line-height:1.6;padding-bottom:70px}
button{font-family:inherit;cursor:pointer;border:none;outline:0}
input,select,textarea{font-family:inherit;font-size:14px;outline:0;background:var(--c2);color:var(--tx);border:1px solid var(--bd);border-radius:8px;padding:9px 11px;width:100%}
input:focus,select:focus,textarea:focus{border-color:var(--ac)}
select{appearance:none;padding-right:28px;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='10' height='10'%3E%3Cpath fill='%23aaa' d='M5 7L0 2h10z'/%3E%3C/svg%3E");background-repeat:no-repeat;background-position:right 10px center}
textarea{resize:vertical;min-height:50px}
.hd{position:sticky;top:0;z-index:100;background:var(--bg);padding:14px 16px 10px;border-bottom:1px solid var(--bd);display:flex;justify-content:space-between;align-items:center}
.hd h1{font-size:18px}
.hd .sub{font-size:11px;color:var(--t3);margin-top:1px}
.tt{width:40px;height:24px;border-radius:20px;background:var(--c2);border:1px solid var(--bd);position:relative}
.qavgbtn.on{background:var(--ac);border-color:var(--ac);color:#fff}
.tt::after{content:'';position:absolute;top:2px;left:2px;width:18px;height:18px;border-radius:50%;background:var(--ac);transition:transform var(--t)}
[data-theme=dark] .tt::after{transform:translateX(16px)}
.tabs{position:fixed;bottom:0;left:0;right:0;z-index:100;background:var(--bg);border-top:1px solid var(--bd);display:flex;justify-content:space-around;padding:5px 0 calc(5px + env(safe-area-inset-bottom))}
.tb{display:flex;flex-direction:column;align-items:center;gap:1px;padding:5px 8px;background:0 0;color:var(--t3);font-size:10px}
.tb.on{color:var(--ac)}
.tb .ic{font-size:18px}
.pg{display:none;padding:14px}
.pg.on{display:block}
.cd{background:var(--c);border-radius:12px;padding:14px;margin-bottom:10px;border:1px solid var(--bd);box-shadow:var(--sh)}
.row{display:flex;gap:8px}
.row>*{flex:1}
.st{display:flex;gap:8px;margin-bottom:12px}
.st .b{flex:1;background:var(--c);border-radius:12px;padding:12px 8px;text-align:center;border:1px solid var(--bd)}
.st .v{font-size:18px;font-weight:700}
.st .v.pk{color:var(--ac)}
.st .v.gn{color:var(--gn)}
.st .v.pp{color:#a78bda}
.st .l{font-size:11px;color:var(--t3);margin-top:3px}
.gh{font-size:12px;font-weight:700;color:var(--ac);padding:14px 0 6px;display:flex;align-items:center;gap:6px}
.gh::before{content:'';width:3px;height:12px;border-radius:2px;background:var(--ac)}
.si{padding:12px;background:var(--c);border-radius:12px;margin-bottom:6px;border:1px solid var(--bd);display:flex;justify-content:space-between;align-items:center;cursor:pointer}
.ii:active,.li:active,.pr:active,.ri:active,.si:active{opacity:.85}
.sn{font-size:14px;font-weight:600}
.sm{font-size:11px;color:var(--t2);margin-top:3px}
.sb{text-align:right}
.sb .am{font-size:15px;font-weight:700;color:var(--gn)}
.sb .su{font-size:10px;color:var(--t3);margin-top:1px}
.badge{font-size:10px;padding:1px 6px;border-radius:10px;background:rgba(232,168,76,.15);color:var(--og);font-weight:600}
.pmu{font-size:10px;color:var(--t3);font-weight:500;margin-right:4px}
.ri{padding:10px 0;border-bottom:1px solid var(--bd);display:flex;justify-content:space-between;align-items:center;cursor:pointer}
.ri:last-child{border:none}
.rt{font-size:13px;font-weight:500}
.rs{font-size:11px;color:var(--t2);margin-top:2px}
.ra{font-weight:700;font-size:13px;white-space:nowrap;margin-left:10px}
.ra.inc{color:var(--gn)}
.ra.exp{color:var(--rd)}
.ra.ref{color:var(--og)}
.tm{font-size:14px;font-weight:700;padding:14px 0 6px}
.pr{display:flex;justify-content:space-between;padding:9px 12px;background:var(--c2);border-radius:8px;margin-bottom:3px;font-size:13px;cursor:pointer}
.pr .pc{color:var(--ac);font-weight:600;white-space:nowrap}
.pt{font-size:12px;font-weight:700;padding:10px 0 4px;color:var(--t2)}
.cki{display:flex;justify-content:space-between;padding:9px 12px;background:var(--c2);border-radius:8px;margin-bottom:4px;cursor:pointer}
.ckr{color:var(--gn);font-weight:600;font-size:13px}
.ii{display:flex;justify-content:space-between;padding:10px 12px;background:var(--c2);border-radius:8px;margin-bottom:5px;cursor:pointer}
.ii .nm{font-size:13px;font-weight:600}
.ii .dt{font-size:11px;color:var(--t2);margin-top:2px}
.ii .am{font-size:14px;font-weight:700;color:var(--gn)}
.isr{display:flex;justify-content:space-between;font-size:12px;color:var(--t2);padding:3px 0}
.isr .v{font-weight:600;color:var(--ac)}
.li{padding:10px 12px;background:var(--c2);border-radius:8px;margin-bottom:5px;cursor:pointer}
.ld{font-size:12px;color:var(--ac);font-weight:600}
.lc{font-size:13px;margin-top:3px;white-space:pre-wrap;word-break:break-word}
.lk{font-size:11px;color:var(--t2);margin-top:2px}
.cr{text-align:center;padding:14px 0;font-size:24px;font-weight:700;color:var(--ac)}
.empty{text-align:center;padding:30px;color:var(--t3)}
.empty .ei{font-size:36px;margin-bottom:6px}
.empty .eh{font-size:12px}
.fab{position:fixed;bottom:68px;right:16px;z-index:90;width:48px;height:48px;border-radius:50%;background:var(--ac);color:#fff;font-size:24px;box-shadow:0 3px 14px rgba(242,126,160,.35);display:flex;align-items:center;justify-content:center;transition:transform .15s}
.fab:active{transform:scale(.9)}
.qm{position:fixed;bottom:126px;right:16px;z-index:95;display:none;flex-direction:column;gap:6px;align-items:flex-end}
.qm.show{display:flex}
.qi{padding:8px 14px;background:var(--c);border:1px solid var(--bd);border-radius:10px;box-shadow:var(--sh);font-size:13px;font-weight:600;white-space:nowrap}
.mo{position:fixed;inset:0;z-index:200;background:rgba(0,0,0,.4);display:none;align-items:flex-end;justify-content:center}
.mo.show{display:flex}
.ml{background:var(--c);border-radius:18px 18px 0 0;width:100%;max-width:480px;max-height:85vh;padding:20px 16px;overflow-y:auto}
.mh{width:32px;height:4px;border-radius:2px;background:var(--bd);margin:0 auto 14px}
.mhd{display:flex;justify-content:space-between;align-items:center;margin-bottom:14px}
.mhd h2{font-size:16px;font-weight:700}
.mc{background:var(--c2);color:var(--t2);width:28px;height:28px;border-radius:50%;font-size:16px;display:flex;align-items:center;justify-content:center}
.fg{margin-bottom:12px}
.fl{font-size:12px;font-weight:600;color:var(--t2);margin-bottom:5px;display:block}
.fh{font-size:11px;color:var(--t3);margin-top:3px}
.cl{display:flex;align-items:center;gap:6px;font-size:13px;cursor:pointer}
.cl input[type=checkbox]{width:auto;accent-color:var(--ac)}
.btn{display:inline-flex;align-items:center;justify-content:center;gap:5px;padding:9px 18px;border-radius:8px;font-size:13px;font-weight:600;transition:all .15s}
.bp{background:var(--ac);color:#fff}
.bd:active,.bg:active,.bp:active{opacity:.85}
.bg{background:0 0;color:var(--ac);border:1px solid var(--bd)}
.bd{background:rgba(224,96,112,.12);color:var(--rd)}
.bs{padding:6px 12px;font-size:12px}
.bb{width:100%}
.sg{display:flex;gap:6px;margin-bottom:10px;flex-wrap:wrap}
.sg .btn.on{background:var(--ac);color:#fff;border-color:var(--ac)}
.qtop{display:flex;justify-content:space-between;align-items:center;gap:8px;margin-bottom:10px}
.qtop .sg{margin-bottom:0}
.qtabs{flex:1}
.qunit{flex-shrink:0}
.qunit .btn{padding:6px 10px}
.co{position:fixed;inset:0;z-index:300;background:rgba(0,0,0,.45);display:none;align-items:center;justify-content:center}
.co.show{display:flex}
.cb{background:var(--c);border-radius:14px;padding:20px;width:260px;text-align:center}
.cb p{font-size:14px;margin-bottom:16px;line-height:1.5}
.cbs{display:flex;gap:8px}
.cbs .btn{flex:1}
.qh{font-size:13px;font-weight:600;color:var(--t2);margin-bottom:10px;display:flex;align-items:center;justify-content:space-between;width:100%}
.qavgbtn{flex:0 0 auto;height:24px;padding:0 10px;margin-left:auto;border-radius:20px;background:var(--c2);color:var(--t2);border:1px solid var(--bd);font-size:10px;line-height:22px;white-space:nowrap}
.qavgbtn.on{background:var(--ac);border-color:var(--ac);color:#fff}
.qrx{padding:10px 12px;background:var(--c2);border-radius:8px;margin-top:8px}
.qrs{display:flex;justify-content:space-between;gap:12px;font-size:12px;color:var(--t2);padding:3px 0}
.qrs .v{font-weight:700;color:var(--ac);text-align:right}
.qrs .g{color:var(--gn)}
.qrs .o{color:var(--og)}
.qsec{display:none}
.qsec.on{display:block}
.qfold{background:var(--c2);border:1px solid var(--bd);border-radius:10px;padding:0 10px;margin:10px 0 12px}
.qfold summary{cursor:pointer;list-style:none;padding:10px 0;font-size:12px;font-weight:700;color:var(--ac);display:flex;justify-content:space-between;align-items:center}
.qfold summary::-webkit-details-marker{display:none}
.qfold summary::after{content:'展开';font-size:11px;color:var(--t3);font-weight:500}
.qfold[open] summary::after{content:'收起'}
.qfold .qfb{padding-bottom:10px}
.cmgrid{display:grid;grid-template-columns:1fr 1fr;gap:12px;align-items:start}
.cmpanel{min-width:0}
.cmpanel .btn{width:100%}
.cmlist{margin-top:10px}
.cmlist .pr{align-items:flex-start;gap:8px}
.cmlist .pr span{word-break:break-word}
[data-theme=dark] .qi{color:#fff}
.cmlist .pr{display:flex;align-items:center}
.cmlist .pr span{flex:1;min-width:0;word-break:break-word}
.cmlist .pr .cm-del{width:auto;flex:0 0 auto;padding:6px 12px}
@media(max-width:520px){.cmgrid{grid-template-columns:1fr}
}
</style>
</head>
<body>
<div class="hd">
<div>
<h1>💰 记账本</h1>
<div class="sub" id="hsub">
</div>
</div>
<button class="tt" onclick="togTh()">
</button>
</div>
<div class="pg on" id="pg0">
</div>
<div class="pg" id="pg1">
</div>
<div class="pg" id="pg2">
<div class="cd">
<div class="row" style="margin-bottom:12px">
<div class="fg" style="margin:0">
<label class="fl">站点代入</label>
<select id="qsite" onchange="qSyncSite()">
</select>
</div>
<div class="fg" style="display:flex;align-items:flex-end;margin:0">
<button class="btn bg bb" onclick="qFillSite()">代入站点汇率</button>
</div>
</div>
<div class="fg" style="margin-bottom:12px">
<label class="fl">全局倍率</label>
<input type="number" id="qmul" step="any" value="1" oninput="qDoAll()">
</div>
<div class="qtop">
<div class="sg qtabs">
<button class="btn bg bs on qtab" onclick="qSw(0)">计费</button>
<button class="btn bg bs qtab" onclick="qSw(1)">汇率</button>
<button class="btn bg bs qtab" onclick="qSw(2)">均值</button>
</div>
<div class="sg qunit">
<button class="btn bg bs qub on" data-u="quota" onclick='qUSw("quota")'>额度</button>
<button class="btn bg bs qub" data-u="yuan" onclick='qUSw("yuan")'>¥</button>
</div>
</div>
<div class="qsec on">
<div class="row" style="margin-bottom:12px">
<div class="fg" style="margin:0">
<select id="qprice" onchange="qFillPrice()">
</select>
</div>
<div class="fg" style="display:flex;align-items:flex-end;margin:0">
<button class="btn bg bb" onclick="qFillPrice()">🪄 代入价格</button>
</div>
</div>
<div class="qh">🩵 按次</div>
<div class="fg">
<label class="fl">每次消耗额度</label>
<input type="number" id="qpc" step="any" oninput="qPer()">
</div>
<div class="qrx" id="qpr" style="display:none">
<div class="qrs">
<span>每次使用额度</span>
<span class="v" id="qpcm">—</span>
</div>
<div class="qrs">
<span>每次费用(¥)</span>
<span class="v" id="qpcy">—</span>
</div>
<div class="qrs">
<span>每元可用次数</span>
<span class="v o" id="qpcp">—</span>
</div>
<div class="qrs">
<span>余额可用次数</span>
<span class="v g" id="qpct">—</span>
</div>
</div>
<div class="qh" style="margin-top:12px">
<span>🩷 按量</span>
<button class="qavgbtn" id="qavgBtn" onclick="qToggleAvg()">qwq</button>
</div>
<div class="row">
<div class="fg">
<label class="fl">输入价(/M)</label>
<input type="number" id="qip" step="any" oninput="qTok()">
</div>
<div class="fg">
<label class="fl">输出价(/M)</label>
<input type="number" id="qop" step="any" oninput="qTok()">
</div>
</div>
<div class="row" style="margin-bottom:10px">
<div class="fg" style="margin:0">
<input type="number" id="qcf" step="any" value="0.3" oninput="qTok()" placeholder="缓存输入价倍率">
</div>
<div class="fg" style="margin:0">
<button class="btn bg bb" id="qcacheBtn" onclick="qTogCache()">缓存：OFF</button>
</div>
</div>
<details class="qfold">
<summary>(ˆつ⩊⊂ˆ)੭</summary>
<div class="qfb">
<div class="row">
<div class="fg">
<label class="fl">提示词(k)</label>
<input type="number" id="qcp" step="any" value="6" oninput="qTok()">
</div>
<div class="fg">
<label class="fl">累计上下文(k)</label>
<input type="number" id="qcap" step="any" value="30" oninput="qSetDriver('cap')">
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">每轮输出最少(k)</label>
<input type="number" id="qomn" step="any" value="0.5" oninput="qTok()">
</div>
<div class="fg">
<label class="fl">每轮输出最多(k)</label>
<input type="number" id="qomx" step="any" value="1.5" oninput="qTok()">
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">预算金额(¥)</label>
<input type="number" id="qbd" step="any" oninput="qSetDriver('budget')">
</div>
<div class="fg">
<label class="fl">预期轮数</label>
<input type="number" id="qrounds" step="any" min="1" oninput="qSetDriver('rounds')">
</div>
</div>
</div>
</details>

<div class="qrx" id="qtr" style="display:none">
<div class="qrs" id="qtcacheRow" style="display:none">
<span>缓存后输入价</span>
<span class="v" id="qtcache">—</span>
</div>
<div class="qrs">
<span>首轮消耗</span>
<span class="v" id="qtyc">—</span>
</div>
<div class="qrs">
<span>末轮消耗</span>
<span class="v" id="qtlast">—</span>
</div>
<div class="qrs">
<span>平均每轮价格</span>
<span class="v o" id="qtavg">—</span>
</div>
<div class="qrs">
<span>累计费用(¥)</span>
<span class="v g" id="qtall">—</span>
</div>
<div class="qrs" id="qctxr" style="display:none">
<span>预期总上下文</span>
<span class="v" id="qctx">—</span>
</div>
<div class="qrs" id="qroundpr" style="display:none">
<span>预期累计价格</span>
<span class="v g" id="qroundprv">—</span>
</div>
<div class="qrs">
<span>预算可用轮数</span>
<span class="v g" id="qtbm">—</span>
</div>
</div>
</div>
<div class="qsec">
<div class="qh">💵 充值比</div>
<div class="row">
<div class="fg">
<label class="fl">实付金额(¥)</label>
<input type="number" id="qy" step="any" oninput='qBase("qy")'>
</div>
<div class="fg">
<label class="fl">获得额度</label>
<input type="number" id="qq" step="any" oninput='qBase("qq")'>
</div>
</div>
<div class="fg">
<label class="fl">实际汇率</label>
<input type="number" id="qrate" step="any" placeholder="请输入" oninput='qBase("qrate")'>
</div>
<div class="qrx" id="qbr" style="display:none">
<div class="qrs">
<span>1元=额度</span>
<span class="v" id="qrd">—</span>
</div>
<div class="qrs">
<span>1额度=元</span>
<span class="v g" id="qry">—</span>
</div>
<div class="qrs" id="qddw" style="display:none">
<span>折扣率</span>
<span class="v o" id="qdd">—</span>
</div>
<div class="qrs" id="qdbrw" style="display:none">
<span>节省金额</span>
<span class="v g" id="qdbr">—</span>
</div>
</div>
<details class="qfold">
<summary>折扣</summary>
<div class="qfb">
<div class="row">
<div class="fg">
<label class="fl">原价金额(¥)</label>
<input type="number" id="qoy" step="any" oninput='qBase("qoy")'>
</div>
<div class="fg">
<label class="fl">折扣率</label>
<input type="number" id="qdisc" step="any" oninput='qBase("qdisc")'>
</div>
</div>
</div>
</details>
<div class="qh" style="margin-top:12px">⏳ 汇率换算</div>
<div class="row" style="margin-bottom:8px">
<div class="fg" style="margin:0">
<select id="calcd" onchange="updCalc()">
<option value="to-q">¥ → 额度</option>
<option value="to-y">额度 → ¥</option>
</select>
</div>
<div class="fg" style="margin:0">
<input type="number" id="calci" placeholder="输入数值" step="any" oninput="updCalc()">
</div>
</div>
<div class="cr" id="calcr">—</div>
</div>
<div class="qsec">
<div class="qh">💖 总额统计</div>
<div class="row">
<div class="fg">
<label class="fl">当前剩余额度</label>
<input type="number" id="qrm" step="any" oninput="qBal()">
</div>
<div class="fg">
<label class="fl">已消耗额度</label>
<input type="number" id="qus" step="any" oninput="qBal()">
</div>
</div>
<div class="qrx" id="qblr" style="display:none">
<div class="qrs" id="qtbqr" style="display:none">
<span>初始总额度</span>
<span class="v o" id="qtbq">—</span>
</div>
<div class="qrs">
<span>剩余额度</span>
<span class="v g" id="qrmy">—</span>
</div>
<div class="qrs" id="quyr" style="display:none">
<span>已消耗额度</span>
<span class="v" id="quy">—</span>
</div>
<div class="qrs" id="qprr" style="display:none">
<span>余额占比</span>
<span class="v g" id="qrpc">—</span>
</div>
</div>
<div class="qh" style="margin-top:12px">✨ 平均用量</div>
<div class="row">
<div class="fg">
<label class="fl">使用天数</label>
<input type="number" id="qad" step="any" oninput="qAvg()">
</div>
<div class="fg">
<label class="fl">总调用次数</label>
<input type="number" id="qac" step="any" oninput="qAvg()">
</div>
</div>
<div class="qrx" id="qavr" style="display:none">
<div class="qrs">
<span>日均消耗额度</span>
<span class="v" id="qadq">—</span>
</div>
<div class="qrs" id="qadyr" style="display:none">
<span>单次费用</span>
<span class="v g" id="qady">—</span>
</div>
<div class="qrs" id="qacdr" style="display:none">
<span>日均调用次数</span>
<span class="v" id="qacd">—</span>
</div>
<div class="qrs" id="qardr" style="display:none">
<span>剩余可用天数</span>
<span class="v g" id="qard">—</span>
</div>
<div class="qrs" id="qartr" style="display:none">
<span>预计用到</span>
<span class="v" id="qart">—</span>
</div>
</div>
<div class="qh" style="margin-top:12px">🎠 Token统计</div>
<div class="row">
<div class="fg">
<label class="fl">已消耗金额(¥)</label>
<input type="number" id="qtm" step="any" oninput="qTokenStat()">
</div>
<div class="fg">
<label class="fl">输入/输出(量比)</label>
<input type="number" id="qtio" step="any" value="7" oninput="qTokenStat()">
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">输入价格(/M)</label>
<input type="number" id="qtip" step="any" oninput="qTokenStat()">
</div>
<div class="fg">
<label class="fl">输出价格(/M)</label>
<input type="number" id="qtop" step="any" oninput="qTokenStat()">
</div>
</div>
<div class="qrx" id="qtsr" style="display:none">
<div class="qrs">
<span>单轮消耗额度</span>
<span class="v" id="qtmq">—</span>
</div>
<div class="qrs">
<span>输入量</span>
<span class="v" id="qtin">—</span>
</div>
<div class="qrs">
<span>输出量</span>
<span class="v g" id="qtout">—</span>
</div>
<div class="qrs">
<span>token总量</span>
<span class="v o" id="qttok">—</span>
</div>
<div class="qrs" id="qtdtr" style="display:none">
<span>日均用量</span>
<span class="v" id="qtdt">—</span>
</div>
</div>
</div>
</div>
</div>
<div class="pg" id="pg3">
<div class="cd">
<div class="sg" id="ptsg">
</div>
<div id="pr-c">
</div>
</div>
</div>
<div class="pg" id="pg4">
</div>
<div class="tabs">
<button class="tb on" data-p="0">
<span class="ic">📋</span>总览</button>
<button class="tb" data-p="1">
<span class="ic">💳</span>充值</button>
<button class="tb" data-p="2">
<span class="ic">⚖️</span>换算</button>
<button class="tb" data-p="3">
<span class="ic">🏷️</span>价格</button>
<button class="tb" data-p="4">
<span class="ic">⚙️</span>更多</button>
</div>
<button class="fab" id="fab" onclick="togQ()">+</button>
<div class="qm" id="qm">
<button class="qi" onclick='opM("site")'>🏠 添加站点</button>
<button class="qi" onclick='opM("rc")'>💳 记录充值</button>
<button class="qi" onclick='opM("pr")'>🏷️ 添加价格</button>
</div>
<div class="mo" id="m-site">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2 id="mst">添加站点</h2>
<button class="mc" onclick='clM("m-site")'>×</button>
</div>
<div class="fg">
<label class="fl">站点名称</label>
<input id="sn">
</div>
<div class="row">
<div class="fg">
<label class="fl">Emoji</label>
<input id="se" maxlength="4">
</div>
<div class="fg">
<label class="fl">分组</label>
<select id="sg">
<option value="other">默认</option>
<option value="A">A组</option>
<option value="B">B组</option>
<option value="C">C组</option>
<option value="D">D组</option>
<option value="E">E组</option>
<option value="F">F组</option>
</select>
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">汇率</label>
<input type="number" id="sr" value="1" step="any">
<div class="fh">
</div>
</div>
<div class="fg">
<label class="fl">换算类型</label>
<select id="sbt">
<option value="yuanToQuota">1R：额</option>
<option value="quotaToYuan">R：1额</option>
</select>
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">当前余额</label>
<input type="number" id="sb" step="any">
</div>
<div class="fg">
<label class="fl">余额单位</label>
<select id="sbu">
<option value="yuan">¥</option>
<option value="usd">$</option>
<option value="quota">额度</option>
</select>
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">历史调用</label>
<input type="number" id="sc">
</div>
<div class="fg">
<label class="fl">历史消耗</label>
<input type="number" id="stc" step="any">
</div>
</div>
<input type="hidden" id="scu" value="same">
<div class="fg">
<label class="fl">入坑时间</label>
<input type="date" id="ssd">
</div>
<div class="fg">
<label class="fl">备注</label>
<input id="sno">
</div>
<input type="hidden" id="sid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="sdl" style="display:none" onclick="dlSite()">删除</button>
<button class="btn bp bb" onclick="svSite()">保存</button>
</div>
</div>
</div>
<div class="mo" id="m-rc">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2 id="mrt">记录充值</h2>
<button class="mc" onclick='clM("m-rc")'>×</button>
</div>
<div class="fg">
<label class="fl">站点</label>
<select id="rs">
</select>
</div>
<div class="row">
<div class="fg">
<label class="fl">金额(¥)</label>
<input type="number" id="ra" step="any">
</div>
<div class="fg">
<label class="fl">日期</label>
<input type="date" id="rd">
</div>
</div>
<div class="fg">
<label class="cl">
<input type="checkbox" id="rrf"> 退款</label>
</div>
<div class="fg">
<label class="fl">备注</label>
<input id="rn">
</div>
<input type="hidden" id="rid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="rdl" style="display:none" onclick="dlRc()">删除</button>
<button class="btn bp bb" onclick="svRc()">保存</button>
</div>
</div>
</div>
<div class="mo" id="m-pr">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2 id="mpt">添加价格</h2>
<button class="mc" onclick='clM("m-pr")'>×</button>
</div>
<div class="fg">
<label class="fl">计费方式</label>
<select id="pty" onchange="togPF()">
<option value="per-call">按次</option>
<option value="per-token">按量</option>
</select>
</div>
<div class="fg">
<label class="fl">站点</label>
<select id="ps" onchange="syncPrModel('mul')">
</select>
</div>
<div class="fg">
<label class="fl">渠道名</label>
<div class="row">
<input id="pch" placeholder="请输入" oninput="pchSyncSel()">
<select id="pchSel" onchange="pchPick()">
</select>
</div>
</div>
<div class="fg">
<label class="fl">模型</label>
<select id="pmo" onchange="syncPrModel('model')">
</select>
</div>
<div id="pfc">
<div class="row">
<div class="fg">
<label class="fl">每次价格</label>
<input type="number" id="ppc" step="any">
</div>
<div class="fg">
<label class="fl">价格单位</label>
<select id="ppu">
<option value="yuan">¥</option>
<option value="usd">$</option>
<option value="quota">额度</option>
</select>
</div>
</div>
</div>
<div id="pft" style="display:none">
<div class="row">
<div class="fg">
<label class="fl">输入价(额度/M)</label>
<input type="number" id="pin" step="any" oninput="syncPrModel('price')">
</div>
<div class="fg">
<label class="fl">输出价(额度/M)</label>
<input type="number" id="pou" step="any" oninput="syncPrModel('price')">
</div>
</div>
<div class="row">
<div class="fg">
<label class="fl">官方输入价(/M)</label>
<input type="number" id="poffIn" step="any" value="5" oninput="syncPrModel('price')">
</div>
<div class="fg">
<label class="fl">官方输出价(/M)</label>
<input type="number" id="poffOut" step="any" value="25" oninput="syncPrModel('price')">
</div>
</div>
<div class="fg">
<label class="fl">倍率</label>
<input type="number" id="pmul" step="any" min="0" oninput="syncPrModel('mul')">
</div>
<div class="fg">
<label class="fl">价格单位</label>
<select id="ptu">
<option value="yuan">¥</option>
<option value="usd">$</option>
<option value="quota">额度</option>
</select>
</div>
<div class="fg">
<label class="cl">
<input type="checkbox" id="pcac"> 带缓存</label>
</div>
</div>
<div class="fg">
<label class="fl">分档</label>
<select id="pti">
<option value="">其他</option>
<option value="🥇">🥇性价比</option>
<option value="🥈">🥈平价</option>
<option value="🥉">🥉小贵</option>
<option value="💸">💸贵</option>
</select>
</div>
<div class="fg">
<label class="fl">备注</label>
<input id="pno">
</div>
<input type="hidden" id="pid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="pdl" style="display:none" onclick="dlPr()">删除</button>
<button class="btn bp bb" onclick="svPr()">保存</button>
</div>
</div>
</div>
<div class="mo" id="m-ck">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2>添加签到</h2>
<button class="mc" onclick='clM("m-ck")'>×</button>
</div>
<div class="fg">
<label class="fl">站点</label>
<select id="cks">
</select>
</div>
<div class="row">
<div class="fg">
<label class="fl">最小收益</label>
<input type="number" id="ckn" step="any">
</div>
<div class="fg">
<label class="fl">最大收益</label>
<input type="number" id="ckx" step="any">
</div>
</div>
<div class="fg">
<label class="fl">收益单位</label>
<select id="cku">
<option value="yuan">¥</option>
<option value="usd">$</option>
<option value="quota">额度</option>
</select>
</div>
  <div class="fg">
  <label class="fl">备注</label>
    <input id="ckno">
    </div>
<input type="hidden" id="ckid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="ckdl" style="display:none" onclick="dlCk()">删除</button>
<button class="btn bp bb" onclick="svCk()">保存</button>
</div>
</div>
</div>
<div class="mo" id="m-iv">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2 id="mit">添加邀请赠金</h2>
<button class="mc" onclick='clM("m-iv")'>×</button>
</div>
<div class="fg">
<label class="fl">类型</label>
<select id="itp" onchange="togIE()">
<option value="promo">推广赠金</option>
<option value="invite">邀请奖励</option>
</select>
</div>
<div class="fg">
<label class="fl">站点</label>
<select id="is">
</select>
</div>
<div class="row">
<div class="fg">
<label class="fl">金额/额度</label>
<input type="number" id="ia" step="any">
</div>
<div class="fg">
<label class="fl">单位</label>
<select id="iu">
<option value="yuan">¥</option>
<option value="usd">$</option>
<option value="quota">额度</option>
</select>
</div>
</div>
<div id="iex">
<div class="row">
<div class="fg">
<label class="fl">邀请人数</label>
<input type="number" id="ic">
</div>
<div class="fg">
<label class="fl">小号数</label>
<input type="number" id="ial">
</div>
</div>
</div>
<div class="fg">
<label class="fl">排名</label>
<select id="irk">
<option value="">无</option>
<option value="🥇">🥇</option>
<option value="🥈">🥈</option>
<option value="🥉">🥉</option>
</select>
</div>
  
<div class="fg">
<label class="fl">备注</label>
<input id="ino">
</div>
<input type="hidden" id="iid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="idl" style="display:none" onclick="dlIv()">删除</button>
<button class="btn bp bb" onclick="svIv()">保存</button>
</div>
</div>
</div>
<div class="mo" id="m-fl">
<div class="ml">
<div class="mh">
</div>
<div class="mhd">
<h2>添加食用日志</h2>
<button class="mc" onclick='clM("m-fl")'>×</button>
</div>
<div class="fg">
<label class="fl">Emoji</label>
<input id="fe" maxlength="4">
</div>
<div class="row">
<div class="fg">
<label class="fl">开始</label>
<input type="date" id="fs">
</div>
<div class="fg">
<label class="fl">结束</label>
<input type="date" id="fn">
</div>
</div>
<div class="fg">
<label class="fl">内容</label>
<textarea id="fc">
</textarea>
</div>
<div class="fg">
<label class="fl">单次成本</label>
<input id="fco">
</div>
<input type="hidden" id="fid">
<div class="row" style="margin-top:6px">
<button class="btn bd bs" id="fdl" style="display:none" onclick="dlFl()">删除</button>
<button class="btn bp bb" onclick="svFl()">保存</button>
</div>
</div>
</div>
<div class="co" id="cfd">
<div class="cb">
<p id="cfm">确认？</p>
<div class="cbs">
<button class="btn bg" onclick="cfN()">取消</button>
<button class="btn bd" onclick="cfY()">确认</button>
</div>
</div>
</div><script>const $=t=>document.getElementById(t),ls=t=>{try{return JSON.parse(localStorage.getItem(t))||[]}catch{return[]}},sv=(t,e)=>localStorage.setItem(t,JSON.stringify(e)),gid=()=>Date.now().toString(36)+Math.random().toString(36).slice(2,7),td=()=>{const t=new Date;return`${t.getFullYear()}-${String(t.getMonth()+1).padStart(2,"0")}-${String(t.getDate()).padStart(2,"0")}`},fN=(t,e)=>{if(null==t||isNaN(t))return"0";const n=parseFloat(t),l=null!=e?Math.min(e,3):Math.abs(n)<1?3:2;return Number.isInteger(n)&&0!==l?n.toString():parseFloat(n.toFixed(l)).toString()},qv=t=>{const e=parseFloat($(t).value);return isNaN(e)?null:e},qf=(t,e)=>{if(null==t||isNaN(t)||!isFinite(t))return"—";const n=+t;if(Number.isInteger(n))return String(n);const l=Math.abs(n)<1?3:2;return parseFloat(n.toFixed(l)).toString()},qtf=t=>{if(null==t||isNaN(t)||!isFinite(t))return"—";const e=+t;return Math.abs(e)>=1e6?fN(e/1e6,2)+"M":Math.abs(e)>=1e3?fN(e/1e3,2)+"k":fN(e,0)};
function qTokenStat(){const t=qv("qtm"),e=qv("qtio"),n=qv("qtip"),l=qv("qtop"),a=qR(),o=qM(),s=qv("qad"),i=(qv("qac"),$("qtsr"));let c=e;if(c>0||(c=7),!(t>0&&n>=0&&l>=0&&a>0))return void(i.style.display="none");const r=t*a,u=((n||0)*c+(l||0))/1e6*o;if(!(u>0))return void(i.style.display="none");const d=r/u,v=d*c,p=v+d;i.style.display="block",$("qtmq").textContent=qf(r),$("qtin").textContent=qtf(v),$("qtout").textContent=qtf(d),$("qttok").textContent=qtf(p),$("qtdtr").style.display=s>0?"flex":"none",s>0&&($("qtdt").textContent=qtf(p/s))}let S=ls("s"),R=ls("r"),P=ls("p"),CK=ls("ck"),F=ls("f"),IV=ls("iv"),CM=ls("cm"),GL=(()=>{try{return JSON.parse(localStorage.getItem("gl"))||{}}catch{return{}}})(); CM=CM.flatMap(t=>t.channel&&t.model?[{id:t.id+"c",channel:t.channel,model:""},{id:t.id+"m",channel:"",model:t.model}]:[t]);const sa=()=>{sv("s",S),sv("r",R),sv("p",P),sv("ck",CK),sv("f",F),sv("iv",IV),sv("cm",CM),sv("gl",GL)};
function togGL(t,e){e&&(e.stopPropagation(),e.preventDefault()),GL[t]=!GL[t],sa(),rOv()}
function gTBUnlocked(){return S.reduce((t,e)=>{const n=e.group||"other";return GL[n]?t:t+bToY(e)},0)}
function gTIUnlocked(){return S.reduce((t,e)=>t+sConsumeY(e),0)+gTBUnlocked()}const thMQ=matchMedia("(prefers-color-scheme:dark)"),sysTh=()=>thMQ.matches?"dark":"light",setTh=t=>document.documentElement.setAttribute("data-theme",t);
function togTh(){setTh("light"===document.documentElement.getAttribute("data-theme")?"dark":"light")}(()=>{localStorage.removeItem("th"),setTh(sysTh());const t=()=>setTh(sysTh());thMQ.addEventListener?thMQ.addEventListener("change",t):thMQ.addListener(t)})(),document.querySelectorAll(".tb").forEach(t=>t.addEventListener("click",()=>{document.querySelectorAll(".tb,.pg").forEach(t=>t.classList.remove("on")),t.classList.add("on"),$("pg"+t.dataset.p).classList.add("on"),clQ()}));let qo=!1;
function togQ(){qo=!qo,$("qm").classList.toggle("show",qo),$("fab").style.transform=qo?"rotate(45deg)":""}
function clQ(){qo=!1,$("qm").classList.remove("show"),$("fab").style.transform=""}document.addEventListener("click",t=>{!qo||t.target.closest("#fab")||t.target.closest("#qm")||clQ()});const opMo=t=>$(t).classList.add("show"),clM=t=>$(t).classList.remove("show");document.querySelectorAll(".mo").forEach(t=>t.addEventListener("click",e=>{e.target===t&&clM(t.id)}));let cfCb=null;
function showCf(t,e){$("cfm").textContent=t,cfCb=e,$("cfd").classList.add("show")}
function cfY(){$("cfd").classList.remove("show"),cfCb&&cfCb(),cfCb=null}
function cfN(){$("cfd").classList.remove("show"),cfCb=null}const gS=t=>S.find(e=>e.id===t),sL=t=>t?(t.emoji||"")+" "+t.name:"未知";
function sOpt(t,e,n){const l=$(t),a=l.value,o=n||a;l.innerHTML=e?'<option value="">全部站点</option>':"",S.filter(t=>{const e=t.group||"other";return"F"!==e&&"E"!==e||o&&t.id===o}).forEach(t=>{const e=document.createElement("option");e.value=t.id,e.textContent=sL(t),l.appendChild(e)}),o&&Array.from(l.options).some(t=>t.value===o)?l.value=o:a&&Array.from(l.options).some(t=>t.value===a)&&(l.value=a),l.value||e||!l.options.length||(l.selectedIndex=0)}
function siteDir(t){return"yuanToQuota"===t?.balanceType?"yuanToQuota":"quotaToYuan"}
function isQuotaUnit(t){return"quota"===t||"usd"===t}

function quotaToY(t,e){const n=parseFloat(t?.rate)||1;return"yuanToQuota"===siteDir(t)?e/n:e*n}

function yuanToQ(t,e){const n=parseFloat(t?.rate)||1;return"yuanToQuota"===siteDir(t)?e*n:e/n}

function unitToY(t,e,n){if(!isFinite(e))return 0;if(isQuotaUnit(n))return quotaToY(t,e);return e}

function unitToQ(t,e,n){if(!isFinite(e))return 0;if(isQuotaUnit(n))return e;return yuanToQ(t,e)}

function bDisp(t){if(!t)return"0￥";const e=parseFloat(t.balance)||0,n=t.balanceUnit||"yuan",l=unitToY(t,e,n);return"quota"===n?`${fN(e)}额  ≈${fN(l)}¥`:"usd"===n?`${fN(e)}$ ≈${fN(l)}¥`:`${fN(e)}¥`}

function gRT(t){return R.filter(e=>!t||e.siteId===t).reduce((t,e)=>t+(parseFloat(e.amount)||0)*(e.refund?-1:1),0)} const gMK=t=>{return t?(e=new Date(t)).getFullYear()+"."+(e.getMonth()+1):"";var e};

function sConsumeY(t){const e=parseFloat(t.totalConsume);if(isNaN(e))return 0;let n=t.consumeUnit||"same";return"same"===n&&(n=t.balanceUnit||"yuan"),unitToY(t,e,n)}

function sAvgCallY(t){const e=parseInt(t.calls)||0,n=sConsumeY(t);return e>0&&n>0?n/e:null}

function bToY(t){if(!t)return 0;return unitToY(t,parseFloat(t.balance)||0,t.balanceUnit||"yuan")} const gTB=()=>S.reduce((t,e)=>t+bToY(e),0);

function bToQ(t){if(!t)return 0;return unitToQ(t,parseFloat(t.balance)||0,t.balanceUnit||"yuan")}

function sConsumeQ(t){const e=parseFloat(t.totalConsume);if(isNaN(e))return 0;let n=t.consumeUnit||"same";return"same"===n&&(n=t.balanceUnit||"yuan"),unitToQ(t,e,n)}
function sInitialY(t){return bToY(t)+sConsumeY(t)}
function dDays(t){if(!t)return null;const e=new Date(t+"T00:00:00"),n=new Date;e.setHours(0,0,0,0),n.setHours(0,0,0,0);const l=Math.floor((n-e)/864e5)+1;return l>0?l:null}
function ivToY(t){const e=gS(t.siteId),n=(e?parseFloat(e.rate):1)||1,l=parseFloat(t.amount)||0;return isQuotaUnit(t.unit)?null!=t.approx?parseFloat(t.approx)||0:quotaToY(e,l):l}
function prSortV(t){
 const site=gS(t.siteId);
 if("per-call"===t.type){
  const price=parseFloat(t.perCall)||0;
  return isQuotaUnit(t.perCallUnit||"yuan")?quotaToY(site,price):price
 }
 let input=parseFloat(t.inputPrice)||0,output=parseFloat(t.outputPrice)||0;
 if(isQuotaUnit(t.tokenUnit)){
  input=quotaToY(site,input);
  output=quotaToY(site,output)
 }
 return input+output
}

function opM(t,e){clQ(),{site:opSite,rc:opRc,pr:opPr,ck:opCk,iv:opIv,fl:opFl}[t](e)}
function opSite(t){const e=!!t;if($("mst").textContent=e?"编辑站点":"添加站点",$("sdl").style.display=e?"":"none",e){const e=gS(t);$("sn").value=e.name||"",$("se").value=e.emoji||"",$("sg").value=e.group||"other",$("sr").value=e.rate||1,
$("sbt").value=e.balanceType==="quotaToYuan"?"quotaToYuan":"yuanToQuota",
$("sb").value=e.balance||"",$("sbu").value=e.balanceUnit||"yuan",$("sc").value=e.calls||"",$("stc").value=e.totalConsume||"",$("scu").value=e.consumeUnit||"same",$("ssd").value=e.startDate||"",$("sno").value=e.note||"",$("sid").value=t}else["sn","se","sb","sc","stc","ssd","sno"].forEach(t=>$(t).value=""),$("sg").value="other",$("sr").value="1",$("sbt").value="yuanToQuota",$("sbu").value="yuan",$("scu").value="same",$("sid").value="";opMo("m-site")}
function svSite(){const t=$("sn").value.trim();if(!t)return alert("请填写名称");const e={name:t,emoji:$("se").value.trim(),group:$("sg").value,rate:parseFloat($("sr").value)||1,balanceType:$("sbt").value,balance:$("sb").value,balanceUnit:$("sbu").value,calls:$("sc").value,totalConsume:$("stc").value,consumeUnit:$("scu").value,startDate:$("ssd").value,note:$("sno").value.trim()},n=$("sid").value;if(n){const t=S.findIndex(t=>t.id===n);t>=0&&(S[t]={...S[t],...e})}else S.push({id:gid(),...e});sa(),clM("m-site"),rAll()}
function dlSite(){const t=$("sid").value;showCf("删除站点？关联的充值/价格/签到/邀请记录不会自动删。",()=>{S=S.filter(e=>e.id!==t),sa(),clM("m-site"),rAll()})}
function opRc(t){const e=!!t;$("mrt").textContent=e?"编辑充值":"记录充值",$("rdl").style.display=e?"":"none";const n=e?R.find(e=>e.id===t):null;sOpt("rs",!1,n?.siteId),e&&n?($("rs").value=n.siteId,$("ra").value=n.amount,$("rd").value=n.date||"",$("rrf").checked=!!n.refund,$("rn").value=n.note||"",$("rid").value=t):($("ra").value="",$("rd").value=td(),$("rrf").checked=!1,$("rn").value="",$("rid").value=""),opMo("m-rc")}
function svRc(){const t=$("rs").value,e=$("ra").value;if(!t||!e)return alert("请填写站点和金额");const n={siteId:t,amount:parseFloat(e),date:$("rd").value,refund:$("rrf").checked,note:$("rn").value.trim()},l=$("rid").value;if(l){const t=R.findIndex(t=>t.id===l);t>=0&&(R[t]={...R[t],...n})}else R.push({id:gid(),...n});sa(),clM("m-rc"),rAll()}
function dlRc(){const t=$("rid").value;showCf("删除充值记录？",()=>{R=R.filter(e=>e.id!==t),sa(),clM("m-rc"),rAll()})}
function togPF(){const t=$("pty").value;$("pfc").style.display="per-call"===t?"":"none",$("pft").style.display="per-token"===t?"":"none"}
function cmSiteOpt(){$("cmps")&&sOpt("cmps",!1)}

function pchPick(){
  const t=$("pchSel"),e=$("pch");
  t&&e&&t.value&&(e.value=t.value)
}

function pchSyncSel(){
  const t=$("pch"),e=$("pchSel");
  if(!t||!e)return;
  const n=t.value.trim();
  e.value=Array.from(e.options).some(t=>t.value===n)?n:""
}

function cmOptForPrice(t,e){
  const n=$("pch"),l=$("pchSel"),a=$("pmo");
  if(!n||!a)return;

  const o=t??n.value,
        s=e??a.value,
        i=[...new Set(CM.map(t=>t.channel).filter(Boolean))],
        c=[...new Set(CM.map(t=>t.model).filter(Boolean))];

  o&&!i.includes(o)&&i.push(o);
  s&&!c.includes(s)&&c.push(s);

  l&&(
    l.innerHTML='<option value="">选择渠道</option>'+i.map(t=>`<option value="${t}">${t}</option>`).join(""),
    l.value=o&&i.includes(o)?o:""
  );

  a.innerHTML='<option value="">请选择模型</option>'+c.map(t=>`<option value="${t}">${t}</option>`).join("");

  n.value=o||"";
  a.value=s&&c.includes(s)?s:""
}
function svCmInline(t){
 const ch="channel"===t,inp=$(ch?"cmch":"cmmo"),hid=$(ch?"cmchid":"cmmid"),btn=$(ch?"cmchsv":"cmmosv"),v=inp.value.trim();
 if(!v)return alert(ch?"请填写渠道名":"请填写模型");
 const id=hid?.value||"";
 const data=ch
  ?{channel:v,model:""}
  :{
    channel:"",
    model:v,
    officialInput:parseFloat($("cmoi")?.value)||0,
    officialOutput:parseFloat($("cmoo")?.value)||0
  };
 if(id){
  const i=CM.findIndex(t=>t.id===id);
  i>=0&&(CM[i]={...CM[i],...data})
 }else CM.push({id:gid(),...data});
 inp.value="";
 hid&&(hid.value="");
 if(!ch){
  $("cmoi")&&($("cmoi").value="");
  $("cmoo")&&($("cmoo").value="");
 }
 btn&&(btn.textContent=ch?"+ 添加渠道":"+ 添加模型");
 sa();
 rAll()
}

function opCmInline(t,e){
 const n=CM.find(e=>e.id===t);if(!n)return;
 if("channel"===e){
  $("cmch").value=n.channel||"";
  $("cmchid").value=t;
  $("cmchsv").textContent="保存渠道"
 }else{
  $("cmmo").value=n.model||"";
  $("cmoi").value=n.officialInput||"";
  $("cmoo").value=n.officialOutput||"";
  $("cmmid").value=t;
  $("cmmosv").textContent="保存模型"
 }
}

function dlCmInline(t){
 if(!t)return;
 const e=CM.find(e=>e.id===t),n=e?e.channel||e.model||"":"";
 confirm("删除这条记录？"+(n?""+n:""))&&(CM=CM.filter(e=>e.id!==t),sa(),rAll())
}

function rCm(){
 const chBox=$("cm-ch-c"),moBox=$("cm-mo-c");if(!chBox||!moBox)return;
 const one=(arr,type)=>arr.length?arr.map(t=>`
  <div class="pr">
   <span class="cm-edit" data-id="${t.id}" data-type="${type}" style="flex:1;min-width:0;cursor:pointer">${"channel"===type?t.channel:t.model}</span>
   <button type="button" class="btn bd bs cm-del" data-id="${t.id}">删</button>
  </div>
 `).join(""):`<div style="color:var(--t3);font-size:13px;padding:8px 0">还没有${"channel"===type?"渠道":"模型"}记录</div>`;
 chBox.innerHTML=one(CM.filter(t=>t.channel),"channel");
 moBox.innerHTML=CM.filter(t=>t.model).length  ?CM.filter(t=>t.model).map(t=>`   <div class="pr">    <span class="cm-edit" data-id="${t.id}" data-type="model" style="flex:1;min-width:0;cursor:pointer">     ${t.model}     <small style="display:block;color:var(--t3);font-weight:400">      官方价 ￥${fN(t.officialInput||0)} / ${fN(t.officialOutput||0)} M     </small>    </span>    <button type="button" class="btn bd bs cm-del" data-id="${t.id}">删</button>   </div>  `).join("")  :`<div style="color:var(--t3);font-size:13px;padding:8px 0">还没有模型记录</div>`;
 document.querySelectorAll(".cm-edit").forEach(t=>t.addEventListener("click",()=>opCmInline(t.dataset.id,t.dataset.type)));
 document.querySelectorAll(".cm-del").forEach(t=>t.addEventListener("click",e=>{e.preventDefault(),e.stopPropagation(),dlCmInline(t.dataset.id)}))
}

function getPrModel(){
 const name=$("pmo")?.value;
 return name?CM.find(t=>t.model===name):null
}

function getPrSite(){
 return gS($("ps")?.value)
}

function prOfficialToPrice(v,site,unit){
 if(!(v>=0))return 0;
 return isQuotaUnit(unit)?yuanToQ(site,v):v
}

function prPriceToOfficial(v,site,unit){
 if(!(v>=0))return 0;
 return isQuotaUnit(unit)?quotaToY(site,v):v
}

function syncPrModel(mode){
 const m=getPrModel(),s=getPrSite(),unit=$("ptu")?.value||"yuan";
 const oiEl=$("poffIn"),ooEl=$("poffOut");
 if(mode==="model"&&m){
  if(!oiEl.value)oiEl.value=m.officialInput||"";
  if(!ooEl.value)ooEl.value=m.officialOutput||"";
 }
 const oi=parseFloat(oiEl?.value)||0;
 const oo=parseFloat(ooEl?.value)||0;
 if(mode==="model"||mode==="mul"){
  const mul=parseFloat($("pmul")?.value);
  if(mul>=0){
   if(oi>0)$("pin").value=qf(prOfficialToPrice(oi*mul,s,unit));
   if(oo>0)$("pou").value=qf(prOfficialToPrice(oo*mul,s,unit));
  }
 }
 if(mode==="price"){
  const pin=parseFloat($("pin")?.value),pou=parseFloat($("pou")?.value);
  let mul=null;
  if(oi>0&&pin>=0)mul=prPriceToOfficial(pin,s,unit)/oi;
  else if(oo>0&&pou>=0)mul=prPriceToOfficial(pou,s,unit)/oo;
  if(null!=mul)$("pmul").value=qf(mul);
 }
}

function opPr(t){const e=!!t;$("mpt").textContent=e?"编辑价格":"添加价格",$("pdl").style.display=e?"":"none";const n=e?P.find(e=>e.id===t):null;sOpt("ps",!1,n?.siteId),cmOptForPrice(n?.channel||"",n?.model||""),e&&n?($("pty").value=n.type||"per-call",$("ps").value=n.siteId,$("pch").value=n.channel||"",$("pmo").value=n.model||"",$("ppc").value=n.perCall||"",$("pin").value=n.inputPrice||"",$("pou").value=n.outputPrice||"",$("poffIn").value=n.officialInput||5,$("poffOut").value=n.officialOutput||25,$("pmul").value=n.multiplier>0?n.multiplier:"",$("ptu").value=n.tokenUnit||"yuan",$("pcac").checked=!!n.hasCache,$("pti").value=n.tier||"",$("pno").value=n.note||"",$("ppu").value=n.perCallUnit||"yuan",$("pid").value=t):(["ppc","pin","pou","pmul","pno"].forEach(t=>$(t).value=""),$("poffIn").value="5",$("poffOut").value="25",cmOptForPrice(),$("pch").value="",$("pchSel")&&($("pchSel").value=""),$("pmo").value="",$("pty").value="per-token",$("ptu").value="yuan",$("pcac").checked=!1,$("pti").value="",$("pid").value="",$("ppu").value="yuan"),togPF(); if(e&&n)syncPrModel("model"); opMo("m-pr")}
function svPr(){const t=$("ps").value;if(!t)return alert("请选择站点");const e={siteId:t,type:$("pty").value,channel:$("pch").value.trim(),model:$("pmo").value.trim(),perCall:parseFloat($("ppc").value)||0,perCallUnit:$("ppu").value,inputPrice:parseFloat($("pin").value)||0, outputPrice:parseFloat($("pou").value)||0, officialInput:parseFloat($("poffIn").value)||0, officialOutput:parseFloat($("poffOut").value)||0, multiplier:parseFloat($("pmul").value)||0, tokenUnit:$("ptu").value,hasCache:$("pcac").checked,tier:$("pti").value,note:$("pno").value.trim()},n=$("pid").value;if(n){const t=P.findIndex(t=>t.id===n);t>=0&&(P[t]={...P[t],...e})}else P.push({id:gid(),...e});sa(),clM("m-pr"),rAll()}
function dlPr(){const t=$("pid").value;showCf("删除价格记录？",()=>{P=P.filter(e=>e.id!==t),sa(),clM("m-pr"),rAll()})}
function opCk(t){const e=!!t;$("ckdl").style.display=e?"":"none";const n=e?CK.find(e=>e.id===t):null;sOpt("cks",!1,n?.siteId),e&&n?($("cks").value=n.siteId,$("ckn").value=n.min||"",$("ckx").value=n.max??"",$("cku").value=n.unit||"yuan",$("ckno").value=n.note||"",$("ckid").value=t):($("ckn").value="",$("ckx").value="",$("cku").value="yuan",$("ckno").value="",$("ckid").value=""),opMo("m-ck")}
function svCk(){const t=$("cks").value;if(!t)return alert("请选择站点");const e=$("ckn").value,n=$("ckx").value,l={siteId:t,min:parseFloat(e)||0,max:""===n?null:parseFloat(n)||0,unit:$("cku").value,note:$("ckno").value.trim()},a=$("ckid").value;if(a){const t=CK.findIndex(t=>t.id===a);t>=0&&(CK[t]={...CK[t],...l})}else CK.push({id:gid(),...l});sa(),clM("m-ck"),rAll()}
function dlCk(){const t=$("ckid").value;showCf("删除签到记录？",()=>{CK=CK.filter(e=>e.id!==t),sa(),clM("m-ck"),rAll()})}let curIT="invite",ivFFold="1"===localStorage.getItem("ivFFold");
function togIvFGroup(){ivFFold=!ivFFold,localStorage.setItem("ivFFold",ivFFold?"1":"0"),rIv()}
function switchIT(t){curIT=t,document.querySelectorAll(".itb").forEach(e=>{const n=e.dataset.type===t;e.classList.toggle("on",n),e.style.background=n?"var(--ac)":"",e.style.color=n?"#fff":"",e.style.borderColor=n?"var(--ac)":""}),rIv()}
function togIE(){$("iex").style.display="invite"===$("itp").value?"":"none"}
function opIv(t){const e=!!t;$("mit").textContent=e?"编辑邀请赠金":"添加邀请赠金",$("idl").style.display=e?"":"none";const n=e?IV.find(e=>e.id===t):null;sOpt("is",!1,n?.siteId),e&&n?($("itp").value=n.type||"promo",$("is").value=n.siteId,$("ia").value=n.amount||"",$("iu").value=n.unit||"yuan",$("ic").value=n.count||"",$("ial").value=n.alts||"",$("irk").value=n.rank||"",$("ino").value=n.note||"",$("iid").value=t):(["ia","ic","ial","ino"].forEach(t=>$(t).value=""),$("iu").value="yuan",$("irk").value="",$("iid").value=""),togIE(),opMo("m-iv")}
function svIv(){const t=$("is").value,e=$("ia").value;if(!t||!e)return alert("请填写站点和金额");const n={type:$("itp").value,siteId:t,amount:parseFloat(e),unit:$("iu").value,count:parseInt($("ic").value)||0,alts:parseInt($("ial").value)||0,rank:$("irk").value,note:$("ino").value.trim(),claimed:true},l=$("iid").value;if(l){const t=IV.findIndex(t=>t.id===l);t>=0&&(IV[t]={...IV[t],...n})}else IV.push({id:gid(),...n});sa(),clM("m-iv"),rAll()}
function dlIv(){const t=$("iid").value;showCf("删除记录？",()=>{IV=IV.filter(e=>e.id!==t),sa(),clM("m-iv"),rAll()})}
function dlFl(t){t&&(t.preventDefault(),t.stopPropagation());const e=$("fid").value;showCf("删除日志？",()=>{F=F.filter(t=>t.id!==e),sa(),clM("m-fl"),rAll()})}
function opFl(t){const e=!!t;if($("fdl").style.display=e?"":"none",e){const e=F.find(e=>e.id===t);$("fe").value=e.emoji||"",$("fs").value=e.start||"",$("fn").value=e.end||"",$("fc").value=e.content||"",$("fco").value=e.cost||"",$("fid").value=t}else["fe","fc","fco"].forEach(t=>$(t).value=""),$("fs").value=td(),$("fn").value="",$("fid").value="";opMo("m-fl")}let flPg=1,flPs=5;
function svFl(){const t=$("fc").value.trim();if(!t)return alert("请填写内容");const e={emoji:$("fe").value.trim(),start:$("fs").value,end:$("fn").value,content:t,cost:$("fco").value.trim()},n=$("fid").value;if(n){const t=F.findIndex(t=>t.id===n);t>=0&&(F[t]={...F[t],...e})}else{const t={id:gid(),...e};F.push(t);const n=[...F].sort((t,e)=>{const n=(e.start||"").localeCompare(t.start||"");return n||((parseInt((e.id||"").slice(0,8),36)||0)-(parseInt((t.id||"").slice(0,8),36)||0))}).findIndex(e=>e.id===t.id);flPg=Math.floor(n/flPs)+1}sa(),clM("m-fl"),rAll()}
function exportD(){const t={s:S,r:R,p:P,ck:CK,f:F,iv:IV,cm:CM,gl:GL,th:document.documentElement.getAttribute("data-theme")||"light",at:(new Date).toISOString()},e=new Blob([JSON.stringify(t)],{type:"application/json;charset=utf-8"}),n=URL.createObjectURL(e),l=document.createElement("a");l.href=n,l.download="api_backup_"+td()+".json",l.style.display="none",document.body.appendChild(l),l.click(),setTimeout(()=>{document.body.removeChild(l),URL.revokeObjectURL(n)},500)}
function importD(t){const e=t.target.files&&t.target.files[0];if(!e)return;const n=new FileReader;n.onload=e=>{try{const t=String(e.target.result||"").replace(/^\uFEFF/,"").trim();if(!t)return alert("文件是空的");const n=JSON.parse(t);showCf("导入会覆盖当前数据，确认？",()=>{S=Array.isArray(n.sites)?n.sites:Array.isArray(n.s)?n.s:[],R=Array.isArray(n.recharges)?n.recharges:Array.isArray(n.r)?n.r:[],P=Array.isArray(n.prices)?n.prices:Array.isArray(n.p)?n.p:[],CK=Array.isArray(n.checkins)?n.checkins:Array.isArray(n.ck)?n.ck:[],F=Array.isArray(n.foodlogs)?n.foodlogs:Array.isArray(n.f)?n.f:[],IV=Array.isArray(n.invites)?n.invites:Array.isArray(n.iv)?n.iv:[],CM=Array.isArray(n.channels)?n.channels:Array.isArray(n.cm)?n.cm:[],GL=n.gl&&"object"==typeof n.gl&&!Array.isArray(n.gl)?n.gl:{};const t=n.theme||n.th;"dark"!==t&&"light"!==t||(document.documentElement.setAttribute("data-theme",t),localStorage.setItem("th",t)),sa(),rAll(),qUSw(qUnit),qCacheUI(),alert("导入完成")})}catch(t){console.error(t),alert("文件格式错误，导入失败")}finally{t.target.value=""}},n.onerror=()=>{alert("读取文件失败"),t.target.value=""},n.readAsText(e)}
function clearAll(){showCf("确认清空所有数据？清空前最好先导出备份。",()=>{S=[],R=[],P=[],CK=[],F=[],IV=[],CM=[],GL={},["s","r","p","ck","f","iv","cm","gl"].forEach(t=>localStorage.removeItem(t)),sa(),rAll(),qUSw(qUnit),qCacheUI(),alert("已清空")})}let curPT="per-token",fFold="1"===localStorage.getItem("fFold");
function togFGroup(){fFold=!fFold,localStorage.setItem("fFold",fFold?"1":"0"),rOv()}
function switchPT(t){curPT=t,document.querySelectorAll("#ptsg .btn").forEach(e=>e.classList.toggle("on",e.dataset.type===t)),rPr()}
function updCalc(){const t=parseFloat($("calci").value),e=$("calcd").value,n=$("calcr"),l=qR();!isNaN(t)&&l>0?n.textContent="to-q"===e?`￥${fN(t)} = ${fN(t*l)}${1===l?"（1:1）":"额"}`:`${fN(t)}额≈￥${fN(t/l)}${1===l?"（1:1）":""}`:n.textContent="—"}let curQTab=0,qFilled=!1,qUnit=localStorage.getItem("qUnit")||"quota",qCacheOn="1"===localStorage.getItem("qCacheOn"),qAvgMode=!1;
function qTogCache(){qCacheOn=!qCacheOn,localStorage.setItem("qCacheOn",qCacheOn?"1":"0"),qCacheUI(),qTok()}

function qToggleAvg(){
 qAvgMode=!qAvgMode;
 const b=$("qavgBtn");
 if(b){
  b.textContent=qAvgMode?"ON":"OFF";
  b.classList.toggle("on",qAvgMode);
 }
 qTok();
}

function qShowRange(a,b,fmt){
 if(null==a||null==b)return"—";
 return qAvgMode?fmt((a+b)/2):a===b?fmt(a):`${fmt(Math.min(a,b))} ～ ${fmt(Math.max(a,b))}`
}

function qCacheUI(){const t=$("qcacheBtn");t&&(t.textContent=qCacheOn?"缓存：ON":"缓存：OFF",t.classList.toggle("on",qCacheOn))}const qQ=()=>{const t=qv("qq");return null!=t&&t>=0?t:null},qM=()=>{const t=qv("qmul");return t&&t>0?t:1};

function qUnitLab(){
 const y="yuan"===qUnit,un=y?"金额(¥)":"额度";
[["qrm",`剩余${un}`],["qus",`已消耗${un}`]].forEach(([i,t])=>{$(i)&&$(i).previousElementSibling&&($(i).previousElementSibling.textContent=t)});
 [["qtbq",y?"初始总金额":"初始总额度"],["qrmy",y?"剩余金额":"剩余额度"],["quy",y?"已消耗金额":"已消耗额度"],["qrpc","余额占比"],["qadq",y?"日均消耗金额":"日均消耗额度"],["qady",y?"单次费用(¥)":"单次额度"],["qtyc",y?"首轮金额":"首轮消耗"],["qtlast",y?"末轮金额":"末轮消耗"],["qtavg",y?"平均每轮单价":"平均每轮额度"],["qtall",y?"累计费用(¥)":"预估总额"]].forEach(([i,t])=>{$(i)&&$(i).parentElement&&($(i).parentElement.firstElementChild.textContent=t)})
}

function qUSw(t){
 const old=qUnit,r=qR();
 if(old!==t&&r>0){
  ["qip","qop"].forEach(id=>{
   const v=qv(id);
   if(null!=v)$(id).value=qf("yuan"===t?v/r:v*r)
  })
 }
 qUnit=t,localStorage.setItem("qUnit",t),document.querySelectorAll(".qub").forEach(e=>e.classList.toggle("on",e.dataset.u===t)),qUnitLab(),qPer(),qTok(),qBal(),qAvg(),qTokenStat()
}

function qFmtUnit(t,e){return null==t||isNaN(t)||!isFinite(t)?"—":"yuan"===qUnit?e>0?qf(t/e):"需填比例":qf(t)}
function qR(){const t=qv("qrate");if(t&&t>0)return t;const e=gS($("qsite")?.value);if(e){const t=parseFloat(e.rate)||0;if(t>0)return t}const n=qv("qy"),l=qv("qq");return n&&n>0&&null!=l&&l>=0?l/n:1}
function qDoAll(){qPer(),qTok(),qBal(),qAvg(),qTokenStat(),updCalc()}
function qSw(t){curQTab=t,document.querySelectorAll(".qtab").forEach((e,n)=>e.classList.toggle("on",t===n)),document.querySelectorAll("#pg2 .qsec").forEach((e,n)=>e.classList.toggle("on",t===n))}

function qSiteOpt(forceId){const t=$("qsite");if(!t)return;const keep=forceId||t.value;t.innerHTML='<option value="__all__">全局</option>';S.filter(x=>{const g=x.group||"other";return g!=="E"&&g!=="F"||x.id===keep}).forEach(x=>{const o=document.createElement("option");o.value=x.id;o.textContent=`${x.emoji||""} ${x.name} (${"yuanToQuota"===siteDir(x)?"1:"+(x.rate||1):(x.rate||1)+":1"})`;t.appendChild(o)});if(keep&&Array.from(t.options).some(o=>o.value===keep))t.value=keep}

function qPriceOpt(){  const t=$("qprice");if(!t)return;
const e=t.value,ty={"per-token":0,"per-call":1},ti={"🥇":0,"🥈":1,"🥉":2,"💸":3,"":4};
const arr=[...P].sort((a,b)=>{
 const x=(ty[a.type]??9)-(ty[b.type]??9);if(x)return x;
 const y=(ti[a.tier||""]??4)-(ti[b.tier||""]??4);if(y)return y;
 const p=prSortV(a)-prSortV(b);if(p)return p;
 const sa=gS(a.siteId),sb=gS(b.siteId),z=(sL(sa)||"").localeCompare(sL(sb)||"");if(z)return z;
 const c=(a.channel||"").localeCompare(b.channel||"");if(c)return c;
 return (a.model||"").localeCompare(b.model||"")
});
t.innerHTML='<option value="">选择价格</option>';  arr.forEach(e=>{   const n=gS(e.siteId),l=document.createElement("option");   l.value=e.id;   const tag=e.tier?` ${e.tier}`:""; l.textContent="per-call"===e.type?`按次 · ${sL(n)} ${e.channel?"["+e.channel+"] ":""}${e.model||""}${tag}`:`按量 · ${sL(n)} ${e.channel?"["+e.channel+"] ":""}${e.model||""}${tag}`;   t.appendChild(l)  });  e&&P.some(t=>t.id===e)&&(t.value=e) }

function qFillPrice(){const id=$("qprice")?.value,p=P.find(x=>x.id===id);if(!p)return; qCacheOn="per-token"===p.type&&!!p.hasCache; localStorage.setItem("qCacheOn",qCacheOn?"1":"0"); qCacheUI();const s=gS(p.siteId),rate=s?yuanToQ(s,1):1;if($("qsite")&&p.siteId){qSiteOpt(p.siteId);$("qsite").value=p.siteId}$("qrate").value=qf(rate);if(s){const l=bToQ(s),a=l+sConsumeQ(s),o=dDays(s.startDate);$("qq").value=a?qf(a):"";$("qrm").value=qf(l);$("qus").value=qf(Math.max(a-l,0));$("qac").value=s.calls||"";$("qtm").value=qf(sConsumeY(s));o&&($("qad").value=o)}if("per-call"===p.type){const v=parseFloat(p.perCall)||0;$("qpc").value=qf("yuan"===p.perCallUnit?v*rate:v);qSw(0);qPer()}else{  const i=parseFloat(p.inputPrice)||0,o=parseFloat(p.outputPrice)||0;  const iy="yuan"===p.tokenUnit?i:i/rate,oy="yuan"===p.tokenUnit?o:o/rate;  $("qip").value=qf("yuan"===qUnit?iy:iy*rate);  $("qop").value=qf("yuan"===qUnit?oy:oy*rate);  qSw(0);qTok() }qBase();qBal();qAvg();qTokenStat();updCalc()}

function qSyncSite(){const t=$("qsite").value;if("__all__"===t){qUSw("yuan");const t=S.reduce((t,e)=>t+sConsumeY(e),0),e=S.reduce((t,e)=>t+(parseInt(e.calls)||0),0),n=gTBUnlocked(),l=t+n,a=S.map(t=>t.startDate).filter(Boolean).sort(),o=a.length?dDays(a[0]):null;$("qrate").value="1";$("qq").value=l?qf(l):"";$("qrm").value=qf(n);$("qus").value=qf(t);$("qac").value=e||"";$("qtm").value=qf(t);o&&($("qad").value=o);qBase();qBal();qAvg();qTokenStat();return}const e=gS(t);if(!e)return qBase();const n=yuanToQ(e,1),l=bToQ(e),a=l+sConsumeQ(e),o=dDays(e.startDate);$("qrate").value=qf(n);$("qq").value=a?qf(a):"";$("qrm").value=qf(l);$("qus").value=qf(Math.max(a-l,0));$("qac").value=e.calls||"";$("qtm").value=qf(sConsumeY(e));o&&($("qad").value=o);qBase();qBal();qAvg();qTokenStat();updCalc()}

function qFillSite(){const t=$("qsite").value;if(qFilled=!0,qUSw("yuan"),"__all__"===t){const t=S.reduce((t,e)=>t+sConsumeY(e),0),e=S.reduce((t,e)=>t+(parseInt(e.calls)||0),0),n=gTBUnlocked(),l=t+n,a=S.map(t=>t.startDate).filter(Boolean).sort(),o=a.length?dDays(a[0]):null;return $("qrate").value="1",$("qoy").value="",$("qy").value="",$("qq").value=l?qf(l):"",$("qrm").value=qf(n),$("qus").value=qf(t),$("qac").value=e||"",$("qtm").value=qf(t),o&&($("qad").value=o),qBase(),qBal(),qAvg(),void qTokenStat()}const e=gS(t);if(!e)return;const n=yuanToQ(e,1),l=bToQ(e),a=l+sConsumeQ(e),o=dDays(e.startDate);$("qrate").value=qf(n),$("qq").value=a?qf(a):"",$("qrm").value=qf(l),$("qus").value=qf(Math.max(a-l,0)),$("qac").value=e.calls||"",$("qtm").value=qf(sConsumeY(e)),o&&($("qad").value=o),qBase(),qBal(),qAvg()}
function qBase(t){const e=t=>(t=>{const e=$(t);return e&&""!==e.value&&!isNaN(parseFloat(e.value))})(t)?parseFloat($(t).value):null,n=(t,e)=>{null!=e&&!isNaN(e)&&isFinite(e)&&($(t).value=qf(e))};let l=e("qoy"),a=e("qdisc"),o=e("qy"),s=e("qq"),i=e("qrate");"qoy"===t?a>0?n("qy",l*a/10):o>0&&l>0&&n("qdisc",o/l*10):"qdisc"===t?l>0?n("qy",l*a/10):o>0&&a>0&&n("qoy",10*o/a):"qy"===t?l>0?n("qdisc",o/l*10):a>0&&n("qoy",10*o/a):!(o>0)&&l>0&&a>0?n("qy",l*a/10):!(a>0)&&l>0&&o>0?n("qdisc",o/l*10):!(l>0)&&o>0&&a>0&&n("qoy",10*o/a),l=e("qoy"),a=e("qdisc"),o=e("qy"),s=e("qq"),i=e("qrate"),"qy"===t?s>0?n("qrate",s/o):i>0&&n("qq",o*i):"qq"===t?o>0?n("qrate",s/o):i>0&&n("qy",s/i):"qrate"===t?o>0?n("qq",o*i):s>0&&n("qy",s/i):!(i>0)&&o>0&&s>0?n("qrate",s/o):!(s>0)&&o>0&&i>0?n("qq",o*i):!(o>0)&&s>0&&i>0&&n("qy",s/i),l=e("qoy"),a=e("qdisc"),o=e("qy");const c=qR();$("qbr").style.display=c?"block":"none",c&&($("qrd").textContent=qf(c),$("qry").textContent=qf(1/c));const r=l>0&&a>0;$("qddw").style.display=r?"flex":"none",r&&($("qdd").textContent=qf(a)+" 折");const u=l>0&&o>0;if($("qdbrw").style.display=u?"flex":"none",u){const t=l-o;$("qdbr").textContent=qf(t)+" 元"}qDoAll()}
function qPer(){const t=qv("qpc"),e=qR(),n=(qQ(),qM()),l=$("qpr");if(!(t>0))return l.style.display="none";const a=t*n;l.style.display="block",$("qpcm").textContent=qf(a),$("qpcy").textContent=e?qf(a/e):"需填比例";const o=qv("qrm");$("qpct").textContent=null!=o&&o>0&&a>0?qf(Math.floor(o/a)):"需填余额",$("qpcp").textContent=e&&a>0?qf(e/a):"—"}
function qRoundQuota(t,e,n,l,a,o=1){if(!(a>0))return null;return((t||0)*(n+l*Math.max(0,a-1))+(e||0)*l)/1e6*o}
function qTotalQuota(t,e,n,l,a,o=1){if(!(a>0))return null;return((t||0)*(n*a+l*(a-1)*a/2)+(e||0)*(l*a))/1e6*o}
function qTotalCost(t,e,n,l,a,o,s=1){const i=qTotalQuota(t,e,n,l,a,s);return null!=i&&o>0?i/o:null}
function qByInputLimit(t,e,n){if(!(t>0&&e>0&&n>=t))return null;const l=Math.floor((n-t)/e)+1;return l>0?l:null}
function qByBudget(t,e,n,l,a,o,s=1){if(!(a>0&&o>0&&n>0&&l>0))return null;let i=0,c=1;for(;c<1e5&&qTotalCost(t,e,n,l,c,o,s)<=a;)c*=2;for(c>1e5&&(c=1e5);i<c;){const r=Math.floor((i+c+1)/2);qTotalCost(t,e,n,l,r,o,s)<=a?i=r:c=r-1}return i>0?i:0}

let qLastDriver=null;
function qSetDriver(d){qLastDriver=d;qTok()}

function qTok(){
 const rawI=qv("qip"),rawO=qv("qop"),n=qv("qcf"),
  a=qv("qcp"),o=qv("qcap"),s=qv("qomn"),i=qv("qomx"),
  c=qv("qbd"),r=qR(),u=qM(),d=$("qtr"),
  needY="yuan"===qUnit,rounds=qv("qrounds");
 const t=null==rawI?null:needY&&r>0?rawI*r:rawI;
 const e=null==rawO?null:needY&&r>0?rawO*r:rawO;
 const l=qCacheOn&&null!=t?t*(null!=n&&n>=0?n:.5):t;
 const fmtCost=v=>{
  if(null==v||isNaN(v)||!isFinite(v))return"—";
  return needY?r>0?qf(v/r):"需填比例":qf(v)
 };
 const fmtTok=v=>null==v||!isFinite(v)?"—":qtf(v);
 const show=(x,y,fmt=fmtCost)=>{
  if(null==x||null==y)return"—";
  if(qAvgMode)return fmt((x+y)/2);
  const mn=Math.min(x,y),mx=Math.max(x,y),lo=fmt(mn),hi=fmt(mx);
  if(mn===mx)return lo;
  if(lo!==hi)return`${lo} ～ ${hi}`;
  if(fmt!==fmtCost)return`${lo} ～ ${hi}`;
  const da=v=>needY?r>0?v/r:null:v;
  const a2=da(mn),b2=da(mx);
  if(null==a2||null==b2)return`${lo} ～ ${hi}`;
  for(let dd=4;dd<=8;dd++){
   const left=parseFloat(a2.toFixed(dd)).toString(),
         right=parseFloat(b2.toFixed(dd)).toString();
   if(left!==right)return`${left} ～ ${right}`
  }
  return`${a2} ～ ${b2}`
 };
 $("qtcacheRow")&&(
  $("qtcacheRow").style.display=qCacheOn&&null!=t?"flex":"none",
  qCacheOn&&null!=t&&($("qtcache").textContent=qf(l)+" / M")
 );
 $("qtall").parentElement.firstElementChild.textContent=needY?"累计费用(¥)":"累计消耗";
 $("qbd").previousElementSibling.textContent=needY?"预算金额(¥)":"预算额度";
 if(!(null!=l&&l>=0||null!=e&&e>=0)||!(null!=a&&a>0)||!(null!=s&&s>0||null!=i&&i>0)){
  d.style.display="none";return
 }
 d.style.display="block";
 const v=1e3*a,
  p=1e3*(null!=s&&s>0?s:i),
  f=1e3*(null!=i&&i>0?i:s);
 const fc1=qRoundQuota(l||0,e||0,v,f,1,u),
       fc2=qRoundQuota(l||0,e||0,v,p,1,u);
 $("qtyc").textContent=show(fc1,fc2);

 const hasRounds=rounds>0,
       hasCap=null!=o&&o>0,
       hasBudget=null!=c&&c>0&&(!needY||r>0);
 let src=null;
 if(qLastDriver==="rounds"&&hasRounds)src="rounds";
 else if(qLastDriver==="cap"&&hasCap)src="cap";
 else if(qLastDriver==="budget"&&hasBudget)src="budget";
 else if(hasRounds)src="rounds";
 else if(hasCap)src="cap";
 else if(hasBudget)src="budget";

 let nA=null,nB=null;
 if(src==="rounds"){nA=nB=rounds}
 else if(src==="cap"){
  const mx=1e3*o;
  nA=qByInputLimit(v,f,mx);nB=qByInputLimit(v,p,mx)
 }else if(src==="budget"){
  const rt=needY?r:1;
  nA=qByBudget(l||0,e||0,v,f,c,rt,u);
  nB=qByBudget(l||0,e||0,v,p,c,rt,u)
 }
 const hasN=nA>0&&nB>0;

 if(hasN){
  const lrA=qRoundQuota(l||0,e||0,v,f,nA,u),
        lrB=qRoundQuota(l||0,e||0,v,p,nB,u);
  $("qtlast").textContent=show(lrA,lrB);
  const totA=qTotalQuota(l||0,e||0,v,f,nA,u),
        totB=qTotalQuota(l||0,e||0,v,p,nB,u);
  $("qtall").textContent=show(totA,totB);
  $("qtavg").textContent=show(totA/nA,totB/nB);
  const cxA=v+f*Math.max(0,nA-1),cxB=v+p*Math.max(0,nB-1);
  $("qctxr").style.display="flex";
  $("qctx").textContent=show(cxA,cxB,fmtTok);
  if(src==="rounds"){
   $("qroundpr").style.display="flex";
   $("qroundpr").firstElementChild.textContent="预期累计价格";
   $("qroundprv").textContent=show(totA,totB)
  }else{
   $("qroundpr").style.display="flex";
   $("qroundpr").firstElementChild.textContent="对应轮数";
   $("qroundprv").textContent=qShowRange(nA,nB,x=>Math.round(x)+" 轮")
  }
 }else{
  $("qtlast").textContent="—";
  $("qtavg").textContent="—";
  $("qtall").textContent="—";
  $("qctxr").style.display="none";
  $("qroundpr").style.display="none"
 }

 if(hasBudget&&src!=="budget"){
  $("qtbm").parentElement.style.display="flex";
  const rt=needY?r:1;
  const bA=qByBudget(l||0,e||0,v,f,c,rt,u),
        bB=qByBudget(l||0,e||0,v,p,c,rt,u);
  $("qtbm").textContent=null!=bA&&null!=bB
   ?qShowRange(bA,bB,x=>Math.round(x)+" 轮"):"—"
 }else{
  $("qtbm").parentElement.style.display="none"
 }
}

function qBal(){
 qUnitLab();const t=$("qball")&&$("qball").checked;let e=qv("qrm"),n=qv("qus");t&&(e=gTBUnlocked(),n=S.reduce((t,e)=>t+sConsumeY(e),0));const l=qR(),a=$("qblr"),o=null!=e&&e>=0,s=null!=n&&n>=0;if(!o&&!s)return a.style.display="none";a.style.display="block",$("qrmy").textContent=o?qFmtUnit(e,l):"—",$("quyr").style.display=s?"flex":"none",$("qtbqr").style.display=s?"flex":"none",$("qprr").style.display=s&&o&&e+n>0?"flex":"none";if(s){const t=(e||0)+n;$("quy").textContent=qFmtUnit(n,l),$("qtbq").textContent=qFmtUnit(t,l),o&&t>0&&($("qrpc").textContent=qf(e/t*100)+"%")}}

function qAvg(){
 qUnitLab();const t=$("qavgall")&&$("qavgall").checked;let e=qv("qus"),n=qv("qad"),l=qv("qac"),a=qv("qrm");t&&(e=S.reduce((t,e)=>t+sConsumeY(e),0),l=S.reduce((t,e)=>t+(parseInt(e.calls)||0),0),a=gTBUnlocked());const o=qR(),s=$("qavr");if(!(e>0&&n>0))return s.style.display="none";s.style.display="block";const i=e/n;$("qadq").textContent=qFmtUnit(i,o);const c=l&&l>0;if($("qadyr").style.display=c?"flex":"none",c){const t=e/l;$("qady").textContent=qFmtUnit(t,o)}const r=l&&l>0;$("qacdr").style.display=r?"flex":"none",r&&($("qacd").textContent=Math.floor(l/n));const u=a&&a>0&&i>0;if($("qardr").style.display=u?"flex":"none",$("qartr").style.display=u?"flex":"none",u){const t=a/i,e=new Date;e.setDate(e.getDate()+Math.floor(t)),$("qard").textContent=Math.floor(t)+"天",$("qart").textContent=`${e.getFullYear()}.${e.getMonth()+1}.${e.getDate()}`}}

function rAll(){rOv(),rRc(),rPr(),rCm(),rMore(),qSiteOpt(),qPriceOpt(),cmOptForPrice(),updCalc(),qBase(),qTokenStat(),qCacheUI()}
function rOv(){const t=S.reduce((t,e)=>t+sConsumeY(e),0),e=S.reduce((t,e)=>t+(parseInt(e.calls)||0),0),n=gTBUnlocked(),l={other:"默认",A:"A组",B:"B组",C:"C组",D:"D组",E:"E组",F:"F组"};let a=`<div class="st"><div class="b"><div class="v pk">¥${fN(t+n)}</div><div class="l">总初始≈</div></div><div class="b"><div class="v gn">¥${fN(t)}</div><div class="l">总消耗≈</div></div><div class="b"><div class="v pp">${e}</div><div class="l">总调用≈</div></div><div class="b"><div class="v pk">¥${fN(n)}</div><div class="l">总余额≈</div></div></div>`;let o=!1;["other","A","B","C","D","E","F"].forEach(t=>{const e=S.filter(e=>(e.group||"other")===t);if(!e.length)return;o=!0;const n=!!GL[t];if("F"===t){if(a+=`<div class="gh" style="cursor:pointer;justify-content:space-between" onclick="togFGroup()">    <span>${l[t]}</span>    <span style="display:flex;align-items:center;gap:8px;font-size:11px;color:var(--t3);font-weight:500">    <span>${fFold?"折叠":"展开"} · ${e.length}</span>      <button class="btn bg bs" style="padding:3px 8px;font-size:11px" onclick="togGL('${t}',event)">${n?"☠️":"🔓"}</button></span></div>`,fFold)return}else a+=`<div class="gh" style="justify-content:space-left">    <span>${l[t]}</span>    <span style="display:flex;align-items:center;gap:8px;font-size:11px;color:var(--t3);font-weight:500">      <button class="btn bg bs" style="padding:3px 8px;font-size:11px" onclick="togGL('${t}',event)">${n?"☠️":"🔓"}</button>    </span>  </div>`;e.forEach(t=>{const e=gRT(t.id),n="",l=sAvgCallY(t),o=parseFloat(t.rate)||1,s=isQuotaUnit(t.consumeUnit)||"same"===t.consumeUnit&&isQuotaUnit(t.balanceUnit),i=t.startDate?` <span style="font-size:11px;color:var(--t3);font-weight:500">入坑 ${(t=>{if(!t)return"";const e=new Date(t+"T00:00:00");return isNaN(e)?t:`${String(e.getFullYear()).slice(2)}.${e.getMonth()+1}.${e.getDate()}`})(t.startDate)}</span>`:"",c=t.note?` <span style="font-size:11px;color:var(--t3);font-weight:500">「${t.note}」</span>`:"";a+=`<div class="si" onclick="opM('site','${t.id}')"><div style="flex:1;min-width:0"><div class="sn">${t.emoji||""} ${t.name} ${n}${i}${c}</div><div class="sm">充值¥${fN(e)}  汇率${"yuanToQuota"===siteDir(t)?"1:"+o:o+":1"}${t.calls?"  调用"+t.calls+"+":""}${null!=l?"  单轮≈"+fN(l,3)+"r":""}</div></div><div class="sb"><div class="am">${bDisp(t)}</div>${t.totalConsume?`<div class="su">初始${fN(sInitialY(t))}r 已用${fN(t.totalConsume)}${s?(("same"===t.consumeUnit?t.balanceUnit:t.consumeUnit)==="usd"?"$":"额"):"r"}</div>`:""}</div></div>`})}),o||(a+='<div class="empty"><div class="ei">🏠</div><div class="eh">还没有站点，点 + 添加</div></div>'),$("pg0").innerHTML=a}
function rRc(){const t=gRT(),e=R.filter(t=>!t.refund).reduce((t,e)=>t+(parseFloat(e.amount)||0),0),n=R.filter(t=>t.refund).reduce((t,e)=>t+(parseFloat(e.amount)||0),0),l=[...R].sort((t,e)=>{const n=(e.date||"").localeCompare(t.date||"");return n||((parseInt((e.id||"").slice(0,8),36)||0)-(parseInt((t.id||"").slice(0,8),36)||0))}),a={};$("hsub").textContent=`总花费 ¥${fN(t)}`,l.forEach(t=>{const e=gMK(t.date)||"未知";(a[e]||(a[e]=[])).push(t)});let o=`<div class="st"><div class="b"><div class="v pk">¥${fN(e)}</div><div class="l">总充值</div></div><div class="b"><div class="v gn">${R.filter(t=>!t.refund).length}</div><div class="l">充值笔数</div></div><div class="b"><div class="v pp">¥${fN(n)}</div><div class="l">已退款</div></div></div>`;Object.entries(a).forEach(([t,e])=>{const n=e.reduce((t,e)=>t+(parseFloat(e.amount)||0)*(e.refund?-1:1),0);o+=`<div class="tm">📅 ${t} <span style="color:var(--rd);font-size:13px;font-weight:500;margin-left:6px">¥${fN(n)}</span></div><div class="cd">`,e.forEach(t=>{const e=gS(t.siteId);o+=`<div class="ri" onclick="opM('rc','${t.id}')"><div style="flex:1;min-width:0"><div class="rt">${sL(e)}</div><div class="rs">${t.date||""} ${t.note?"· "+t.note:""}</div></div><div class="ra ${t.refund?"ref":"inc"}">${t.refund?"+":"-"} ${fN(t.amount)} ¥</div></div>`}),o+="</div>"}),R.length||(o+='<div class="empty"><div class="ei">💳</div><div class="eh">还没有充值记录</div></div>'),$("pg1").innerHTML=o}

function rPr(){
 if($("ptsg").innerHTML=`
    <button class="btn bg bs ${"per-call"===curPT?"on":""}" data-type="per-call" onclick="switchPT('per-call')">按次</button>
    <button class="btn bg bs ${"per-token"===curPT?"on":""}" data-type="per-token" onclick="switchPT('per-token')">按量</button>
    <button class="btn bg bs ${"cm"===curPT?"on":""}" data-type="cm" onclick="switchPT('cm')">仓库</button>
  `,"cm"===curPT)return $("pr-c").innerHTML=`
    <div class="cmgrid">
      <div class="cmpanel">
        <div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:8px">💭 渠道库</div>
        <div class="fg"><input id="cmch" placeholder="渠道名"></div>
        <input type="hidden" id="cmchid">
        <button class="btn bg bs" id="cmchsv" onclick='svCmInline("channel")'>+ 添加渠道</button>
        <div id="cm-ch-c" class="cmlist"></div>
      </div>
      <div class="cmpanel">
  <div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:8px">💬 模型库</div>
  <div class="fg"><input id="cmmo" placeholder="模型"></div>
  <div class="row">
    <div class="fg"><label class="fl">官方输入价(/M)</label><input type="number" id="cmoi" step="any" placeholder="例 5"></div>
    <div class="fg"><label class="fl">官方输出价(/M)</label><input type="number" id="cmoo" step="any" placeholder="例 25"></div>
  </div>
  <input type="hidden" id="cmmid">
  <button class="btn bg bs" id="cmmosv" onclick='svCmInline("model")'>+ 添加模型</button>
  <div id="cm-mo-c" class="cmlist"></div>
</div>
    </div>
  `,void rCm();
 const t=P.filter(t=>t.type===curPT).sort((t,e)=>prSortV(t)-prSortV(e)),e={"🥇":"🥇性价比","🥈":"🥈平价","🥉":"🥉小贵","💸":"💸 贵","":"其他"};let n="";["🥇","🥈","🥉","💸",""].forEach(l=>{const a=t.filter(t=>(t.tier||"")===l);a.length&&(n+=`<div class="pt">${e[l]}</div>`,a.forEach(t=>{const e=gS(t.siteId),l=(e?parseFloat(e.rate):1)||1;let a="";  if("per-call"===t.type){const v=parseFloat(t.perCall)||0;a=isQuotaUnit(t.perCallUnit||"yuan")?`${fN(v,4)}${"usd"===t.perCallUnit?" $":"额"}/次 ≈￥${fN(quotaToY(e,v),4)}/次`:`￥${fN(v,4)}/次`}else{const e=parseFloat(t.inputPrice)||0,n=parseFloat(t.outputPrice)||0,u=t.tokenUnit||"yuan";if(isQuotaUnit(u)){const s=quotaToY(e?gS(t.siteId):null,e),i=quotaToY(n?gS(t.siteId):null,n);a=`${t.hasCache?"[缓] ":""}<span style="font-size:12px">${"usd"===u?"$":""} ${fN(e)} / ${fN(n)} ${"usd"===u?"":"额"} ≈</span>￥${fN(s)} / ${fN(i)} M`}else a=`${t.hasCache?"[缓] ":""}${"usd"===u?"$":"￥"}${fN(e)} / ${fN(n)} M`}n+=`<div class="pr"
 
onclick="opM('pr','${t.id}')">        <span style="flex:1;min-width:0">          ${sL(e)}          ${t.channel?"["+t.channel+"]":""}          ${t.model?'<span style="color:var(--ac);font-size:11px;font-weight:600"> '+t.model+"</span>":""}          ${t.multiplier>0?`<span style="color:var(--ac);font-size:10px;background:var(--c2);border:1px solid var(--bd);border-radius:6px;padding:1px 5px;margin-left:4px">${fN(t.multiplier)}x</span>`:""}${t.note?'<span style="color:var(--t3);font-size:11px;margin-left:4px">'+t.note+"</span>":""}        </span>        <span class="pc">${a}</span>      </div>`}))}),$("pr-c").innerHTML=t.length?n:'<div class="empty"><div class="ei">🏷️</div><div class="eh">还没有价格记录</div></div>'}

function rIv(){const t=IV.filter(t=>t.type===curIT),e={"🥇":0,"🥈":1,"🥉":2};t.sort((t,n)=>(e[t.rank]??99)!==(e[n.rank]??99)?(e[t.rank]??99)-(e[n.rank]??99):ivToY(n)-ivToY(t));const n=t=>{const e=gS(t.siteId);return"F"===(e?.group||"other")},l=t.filter(t=>!n(t)),a=t.filter(t=>n(t)),o=t=>{const e=gS(t.siteId),n=ivToY(t),l=parseFloat(t.amount)||0,a="invite"===t.type?(s=[t.count?t.count+"人":"",t.alts?"含"+t.alts+"小号":""].filter(Boolean)).length?"（"+s.join(" ")+"）":"":"",o=isQuotaUnit(t.unit)?`${fN(l)}${"usd"===t.unit?"$":"额"} ≈${fN(n)}¥`:`${fN(n)}¥`;var s;return`<div class="ii" onclick="opM('iv','${t.id}')" style="${t.claimed?"":"opacity:.5"}">    <div style="flex:1;min-width:0">      <div class="nm">${sL(e)} ${"promo"===curIT?"推广":"邀请"} ${t.rank||""}</div>      <div class="dt">${a} ${t.note||""} </div>    </div>    <div style="text-align:right;flex-shrink:0;margin-left:10px">      <div class="am">${o}</div>    </div>  </div>`};let s="";l.forEach(t=>{s+=o(t)}),a.length&&(s+=`<div class="gh" onclick="togIvFGroup()" style="cursor:pointer;justify-content:space-between;margin-top:8px">      <span>F组</span>      <span style="font-size:11px;color:var(--t3);font-weight:500">${ivFFold?"折叠":"展开"} · ${a.length}</span>    </div>`,ivFFold||a.forEach(t=>{s+=o(t)})),$("ivls").innerHTML=t.length?s:`<div style="color:var(--t3);font-size:13px;padding:8px 0">${"promo"===curIT?"还没有推广赠金记录":"还没有邀请奖励记录"}</div>`;let i="";if("invite"===curIT&&t.length){const e=t.reduce((t,e)=>t+ivToY(e),0),n=t.reduce((t,e)=>t+(parseInt(e.count)||0),0),l=t.reduce((t,e)=>t+(parseInt(e.alts)||0),0);i+=`<div class="isr"><span>邀请总收益</span><span class="v">${fN(e)}¥</span></div>      <div class="isr"><span>总邀请</span><span class="v">${n}人（含${l}小号）</span></div>`}if("promo"===curIT&&t.length){const e=t.filter(t=>t.claimed).reduce((t,e)=>t+ivToY(e),0);i+=`<div class="isr"><span>推广总收益</span><span class="v">${fN(e)}¥</span></div>`}$("ivsm").innerHTML=i}
function goFlPg(t){const e=Math.max(1,Math.ceil(F.length/flPs));flPg=Math.max(1,Math.min(e,t)),rMore()}
function rMore(){let t="";CK.forEach(e=>{const n=gS(e.siteId),l=(n?parseFloat(n.rate):1)||1,a=parseFloat(e.min)||0,o=null==e.max||""===e.max?null:parseFloat(e.max);let s;s=isQuotaUnit(e.unit)?null==o||o===a?`${fN(a)}${"usd"===e.unit?"$":"额"} ≈${fN(a/l)}¥`:`${fN(a)}～${fN(o)}${"usd"===e.unit?"$":"额"} ≈${fN(a/l)}～${fN(o/l)}¥`:null==o||o===a?`${fN(a)}¥`:`${fN(a)}～${fN(o)}¥`,t+=`<div class="cki" onclick="opM('ck','${e.id}')"><span>${sL(n)}${e.note?'<span style="font-size:11px;color:var(--t3);margin-left:4px">'+e.note+"</span>":""}</span><span class="ckr">${s}</span></div>`}),CK.length||(t='<div style="color:var(--t3);font-size:13px;padding:8px 0">还没有签到记录</div>');const e=[...F].sort((t,e)=>{const n=(e.start||"").localeCompare(t.start||"");return n||((parseInt((e.id||"").slice(0,8),36)||0)-(parseInt((t.id||"").slice(0,8),36)||0))}),n=Math.max(1,Math.ceil(e.length/flPs));flPg>n&&(flPg=n);const l=e.slice((flPg-1)*flPs,(flPg-1)*flPs+flPs);let a="";l.forEach(t=>{const e=t.start?t.start.replace(/-/g,".")+(t.end?"～"+t.end.replace(/-/g,"."):"～"):"";a+=`<div class="li" onclick="opM('fl','${t.id}')"><div class="ld">${t.emoji||"📝"} ${e}</div><div class="lc">${t.content}</div>${t.cost?'<div class="lk">'+t.cost+"</div>":""}</div>`}),F.length?a+=`<div style="display:flex;align-items:center;justify-content:space-between;gap:8px;margin-top:8px"><button class="btn bg bs" ${flPg<=1?'disabled style="opacity:.45;pointer-events:none"':""} onclick="goFlPg(${flPg-1})">上一页</button><div style="font-size:12px;color:var(--t2)">第 ${flPg} / ${n} 页</div><button class="btn bg bs" ${flPg>=n?'disabled style="opacity:.45;pointer-events:none"':""} onclick="goFlPg(${flPg+1})">下一页</button></div>`:a='<div style="color:var(--t3);font-size:13px;padding:8px 0">还没有食用日志</div>',$("pg4").innerHTML=`<div class="cd"><div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:10px">📅 签到概览</div>${t}<button class="btn bg bs" style="margin-top:6px" onclick="opM('ck')">+ 添加签到</button></div><div class="cd"><div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:10px">✨ 邀请赠金</div><div class="sg"><button class="btn bg bs itb ${"promo"===curIT?"on":""}" data-type="promo" onclick="switchIT('promo')">推广赠金</button><button class="btn bg bs itb ${"invite"===curIT?"on":""}" data-type="invite" onclick="switchIT('invite')">邀请奖励</button></div><div id="ivls"></div><div id="ivsm" style="margin-top:6px"></div><button class="btn bg bs" style="margin-top:6px" onclick="opM('iv')">+ 添加记录</button></div><div class="cd"><div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:10px">📝 食用日志</div>${a}<button class="btn bg bs" style="margin-top:6px" onclick="opM('fl')">+ 添加日志</button></div><div class="cd"><div style="font-size:13px;font-weight:600;color:var(--t2);margin-bottom:10px">💾 数据管理</div><div style="display:flex;gap:8px;flex-wrap:wrap"><label class="btn bg bs" style="cursor:pointer">📥 导入<input type="file" accept=".json" style="display:none" onchange="importD(event)"></label><button class="btn bg bs" onclick="exportD()">📤 导出</button><button class="btn bd bs" onclick="clearAll()">🗑️ 清空</button></div><div class="fh" style="margin-top:6px">JSON格式备份/恢复</div></div>`,rIv()}rAll(),qUSw(qUnit),qCacheUI()</script>
</body>
</html>
```
