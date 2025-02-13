// ==UserScript==
// @name        Bad Iine Data Cleaner
// @namespace        http://tampermonkey.net/
// @version        0.4
// @description        ブログ削除されたIDのブロック登録を削除して最適化する
// @author        Ameba Blog User
// @match        https://ameblo.jp/*
// @match        https://blog.ameba.jp/ucs/top*
// @exclude        https://ameblo.jp/*/image*
// @icon        https://www.google.com/s2/favicons?sz=64&domain=ameba.jp
// @noframes
// @updateURL        https://github.com/personwritep/Bad_Iine_Data_Cleaner/raw/main/Bad_Iine_Data_Cleaner.user.js
// @downloadURL        https://github.com/personwritep/Bad_Iine_Data_Cleaner/raw/main/Bad_Iine_Data_Cleaner.user.js
// ==/UserScript==



let iine_block_data={}; // 総合ブロックデータ
let iine_block_data_temp; // 処理用の仮ブロックデータ
let iine_block_data_clean; // 処理後のブロックデータ

let iine_block_id=[];
let iine_block_img=[];
let block_filter_id;
let block_regex_id;
let block_filter_img;
let block_regex_img;



let searchParams=new URLSearchParams(window.location.search);
let action=0;
if(searchParams.has('bidc')){
    action=searchParams.get('bidc'); }



let svg_path=
    '<path d="M35 1C19 3 6 15 1 31C-2 46 0 64 0 79L0 170C0 '+
    '188 -3 208 8 223C21 241 40 240 60 240L156 240C172 240 189 242 205 '+
    '240C221 236 234 225 239 209C243 195 240 177 240 162L240 68C240 51 '+
    '243 31 232 16C218 -2 198 0 178 0L83 0C67 0 50 -2 35 0z"/>'+
    '<path style="fill:#fff" d="M39 6C24 9 11 18 8 33C4 48 6 65 6 80L6 169C6 '+
    '186 3 206 14 220C26 236 46 234 64 234L156 234C172 234 189 236 205 '+
    '233C221 230 231 217 234 202C236 188 234 172 234 158L234 71C234 54 '+
    '237 33 226 19C213 4 193 6 175 6L85 6C70 6 54 4 39 6z"/>'+
    '<path d="M44 214C83 214 123 212 161 202C181 197 '+
    '201 189 213 171C222 157 223 134 213 119C201 101 173 92 153 102C153 '+
    '81 147 59 132 43C106 17 58 11 36 45C27 58 25 75 24 90C21 122 28 156 '+
    '36 187C38 196 42 205 44 214z"/>'+
    '<path style="fill:#fff" d="M67 84C58 86 53 97 59 105C63 110 70 112 76 '+
    '110C95 105 85 79 67 84M101 86L101 196C107 196 114 194 120 194L120 '+
    '181C124 185 128 188 133 190C137 191 140 191 144 191C173 189 181 153 '+
    '175 130C170 113 156 103 139 109C133 111 128 115 124 119L124 83C116 '+
    '83 109 86 101 86M60 124L60 203C67 203 74 201 81 200L81 121C74 122 '+
    '67 124 60 124z"/>'+
    '<path d="M136 125C121 129 120 152 124 164C126 171 '+
    '134 178 142 175C157 171 159 150 155 137C153 128 145 122 136 125z"/>';

let svg_mark_t=
    '<svg class="svgm_t" width="24" height="24" viewBox="0 0 240 240" '+
    'style="margin: -6px 12px -5px -6px; fill: #2196f3;">'+ svg_path +'</svg>';



if(document.domain.includes('ameba') && action==0){ //「管理画面」でのみ開始出来る
    panel_disp();
    if(read_local()){

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '❶ ブロックデータをファイル保存する　'+
            '管理画面の登録: <span class="now_item"></span>'+
            '<input class="execute" type="submit" value="保存する">';

        let text=
            'ここでは「管理画面」のブロックデータをファイルに保存します<br>'+
            '　▪通常はPCの「ダウンロード」フォルダにファイルが保存されます<br>'+
            '　▪ファイル名は「n」を連番数とした「<b>iine_mute(n).json</b>」になります';
        help(text, 0);

        let now_item=document.querySelector('.now_item');
        now_item.textContent=iine_block_data.length -2;
        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');


        execute.onclick=function(){
            backup('iine_mute.json');
            setTimeout(()=>{
                ucs_act();
            }, 1000 ); }

        end_task.onclick=function(){
            close_pannel(); }


        function ucs_act(){
            bidc_inner.innerHTML=
                '❷ ファイル保存が完了したら「ブログ画面」に移動します'+
                '<input class="execute" type="submit" value="ブログ画面を開く">';

            let text=
                'ファイル保存が完了するのに数秒かかる場合があります<br>'+
                '完了が確実になってから「ブログ画面を開く」を押してください';
            help(text, 0);


            let execute=document.querySelector('.execute');
            execute.onclick=function(){
                open_blog(1); }}

    }} // action==0



if(action==1){
    panel_disp();
    if(read_local()){

        reg_set();

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '❸ 保存した最新の「iine_mute(n).json」を読込む'+
            '<input class="execute" type="submit" value="ファイルを読込む">'+
            '<input class="file_read" type="file">';

        let text=
            'ファイルを指定するサブウインドウが表示されたら、次の操作をしてください<br>'+
            '　▪「マイコンピューター」の中の「ダウンロード」フォルダを探します<br>'+
            '　　（場合により「ダウンロード」が最初から開いているかも知れません）<br>'+
            '　▪「ダウンロード」を開き「<b>iine_mute(n).json</b>」のファイルを探します<br>'+
            '　▪連番ファイルが複数ある場合は、最新の「更新日付」のものを選択します<br>'+
            '　　（これは先ほど保存した「管理画面」のブロックデータのファイルです）<br>'+
            '　▪ファイルを選択したら、サブウインドウの下端の「開く」を押します';
        help(text, 0);

        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');
        let file_read=document.querySelector('.file_read');


        execute.onclick=function(){
            read_backup(file_read, 1, 2); } //「1」差分追加 「2」次の処理

        end_task.onclick=function(){
            close_pannel(); }

    }} // action==1



if(action==2){
    panel_disp();
    if(read_local()){

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '❹ 統合した現在のブロック登録：<span class="now_item"></span>'+
            '<input class="execute" type="submit" value="最適化処理に進む">';

        let text=
            '以上で「管理画面」「ブログページ」のブロックデータが統合されました<br>'+
            '　▪現在のブロック登録の表示は、統合した結果の登録数です';
        help(text, 0);

        let now_item=document.querySelector('.now_item');
        now_item.textContent=iine_block_data.length -2;
        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');


        execute.onclick=function(){
            reload_q(3); }

        end_task.onclick=function(){
            close_pannel(); }

    }} // action==2



if(action==3){
    panel_disp();
    if(read_local()){

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '➎ 現在のブロック登録：<span class="now_item"></span>　'+
            '削除する不要登録：<span class="delete_item"></span>'+
            '<input class="execute" type="submit" value="">';

        let now_item=document.querySelector('.now_item');
        let delete_item=document.querySelector('.delete_item');
        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');


        iine_block_data_temp=iine_block_data;

        for(let k=2; k<iine_block_data_temp.length; k++){ // 2以上で実行に注意
            cleaning(k); }
        iine_block_data_clean=iine_block_data_temp.filter(function(item){
            return item[0]!='deleted'; });

        now_item.textContent=iine_block_data_temp.length-2;
        let deleted=iine_block_data_temp.length - iine_block_data_clean.length;
        delete_item.textContent=deleted;

        if(deleted==0){
            execute.value='次に進む';
            let text=
                '現在の「ブロックデータ」に無効なIDはありませんでした<br>'+
                '次のファイル保存の処理に進んでください';
            help(text, 0); }
        else{
            execute.value='最適化を実行する';
            let text=
                '「ブロックデータの最適化」の処理は、以下の内容です<br>'+
                '　▪ユーザーの退会によって無効になったIDをチェック<br>'+
                '　▪ブロックデータから、無効なIDの登録を削除<br>'+
                '「最適化」の処理によって、ブロック登録数が減ります';
            help(text, 0); }


        execute.onclick=function(){
            iine_block_data=iine_block_data_clean;
            write_local();
            reload_q(4); }

        end_task.onclick=function(){
            close_pannel(); }

        function cleaning(k){
            let url='https://ameblo.jp/'+ iine_block_data_temp[k][0];
            if(check(url)){
                iine_block_data_temp[k][0]='deleted'; }

            function check(target_url){
                if(load(target_url)!=200){
                    return true; } // target_urlが無い時に true
                function load(_url){
                    let xhr;
                    xhr=new XMLHttpRequest();
                    xhr.open("HEAD", _url, false); //同期モード
                    xhr.send();
                    return xhr.status; }}}

    }} // action==3



if(action==4){
    panel_disp();
    if(read_local()){

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '❻ 現在のブロック登録：<span class="now_item"></span>'+
            '<input class="execute" type="submit" value="最適化したデータをファイル保存する">';

        let text=
            '「ブログページ」の最新のブロックデータをファイル保存します<br>'+
            '　▪通常はPCの「ダウンロード」フォルダにファイルが保存されます<br>'+
            '　▪ファイル名は「n」を連番数とした「<b>iine_mute_clean(n).json</b>」です';
        help(text, 0);

        let now_item=document.querySelector('.now_item');
        now_item.textContent=iine_block_data.length -2;
        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');


        execute.onclick=function(){
            backup('iine_mute_clean.json'); // ファイル名「iine_mute_clean.json」
            setTimeout(()=>{
                blog_act();
            }, 1000 ); }

        end_task.onclick=function(){
            close_pannel(); }


        function blog_act(){
            bidc_inner.innerHTML=
                '➐ ファイル保存が完了したら「管理画面」に移動します'+
                '<input class="execute" type="submit" value="管理画面を開く">';

            let text=
                'ファイル保存が完了するのに数秒かかる場合があります<br>'+
                '完了が確実になってから「管理画面を開く」を押してください';
            help(text, 0);


            let execute=document.querySelector('.execute');
            execute.onclick=function(){
                open_ucs(5); }}

    }} // action==4



if(action==5){
    panel_disp();
    if(read_local()){

        reg_set();

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '❽ 最新の「iine_mute_clean(n).json」を読込む'+
            '<input class="execute" type="submit" value="ファイルを読込む">'+
            '<input class="file_read" type="file">';

        let text=
            'ファイルを指定するサブウインドウが表示されたら、次の操作をしてください<br>'+
            '　▪「マイコンピューター」の中の「ダウンロード」フォルダを探します<br>'+
            '　　（場合により「ダウンロード」が最初から開いているかも知れません）<br>'+
            '　▪「<b>iine_mute_clean(n).json</b>」のファイルを探します<br>'+
            '　▪連番ファイルが複数ある場合は、最新の「更新日付」のものを選択します<br>'+
            '　　（このファイルの内容は「ブログぺージ」の最新のブロックデータです）<br>'+
            '　▪ファイルを選択したら、サブウインドウの下端の「開く」を押します';
        help(text, 0);

        let execute=document.querySelector('.execute');
        let end_task=document.querySelector('.end_task');
        let file_read=document.querySelector('.file_read');

        execute.onclick=function(){
            read_backup(file_read, 0, 6); } //「0」上書き読込み 「6」次の処理

        end_task.onclick=function(){
            close_pannel(); }

    }} // action==5



if(action==6){
    panel_disp();
    if(read_local()){

        history.pushState('0', '0', location.href.replace(/\?.*$/, ''));

        let bidc_span=document.querySelector('.bidc_span');
        bidc_span.innerHTML=
            svg_mark_t +'Bad Iine Data Cleaner'+
            '<input class="bidc_help" type="submit" value="説明">';

        let bidc_help=document.querySelector('.bidc_help');
        bidc_help.style.display='none';
        let svg=
            '<svg height="20px" style="enable-background: new 80 80 160 160; '+
            'vertical-align: -5px;" viewbox="80 80 160 160" width="24px" x="0px" y="0px">'+
            '<style>.st0 { fill: none; stroke: #333; stroke-width: 12; stroke-linecap: round; '+
            'stroke-linejoin: round; stroke-miterlimit: 12; }</style>'+
            '<path class="st0" d="M198.04 167.1c-7.52 27.06-35.56 42.91-62.63 '+
            '35.38s-42.91-35.56-35.38-62.63s35.56-42.91 62.63-35.38 '+
            'c13.25 3.68 23.81 12.28 30.25 23.28">'+
            '</path><polyline class="st0" points="170.5,124.69 193.61,129.44 194.62,105.87">'+
            '</polyline></svg>';

        let text=
            '▶ ブロックデータのメンテナンスを終了する場合<br>'+
            '　「Tampermonkey」のダッシュボードでこのツールを「OFF」にします<br><br>'+
            '▶ ブロックデータのメンテナンスをやりなおす場合<br>'+
            '　 ブラウザの更新ボタン'+ svg +'で このページをリロードしてください';
        help(text, 1);

        let bidc_inner=document.querySelector('.bidc_inner');
        bidc_inner.innerHTML=
            '➒ ブロックデータの同期と最適化が完了しました　　'+
            '現在のブロック登録：<span class="now_item"></span>';

        let now_item=document.querySelector('.now_item');
        now_item.textContent=iine_block_data.length -2;

    }} // action==6



//======== Common Functions ====================

function open_ucs(n){
    let url='https://blog.ameba.jp/ucs/top.do?bidc='+ n;
    location.href=url; }



function open_blog(n){
    let id=document.querySelector('.amebaId');
    if(id){
        id=id.textContent;
        let url='https://ameblo.jp/'+ id +'?bidc='+ n;
        location.href=url; }}



function reload_q(n){
    let url=location.href.replace(/\?.*$/, '') + '?bidc='+ n;
    location.href=url; }



function panel_disp(){

    let panel=
        '<div id="bidc_panel">'+
        '<span class="bidc_span">'+ svg_mark_t +'Bad Iine Data Cleaner'+
        '<input class="bidc_help" type="submit" value="説明">'+
        '<input class="end_task" type="submit" value="処理終了"></span>'+
        '<div class="bidc_inner"></div>'+
        '<div class="bidc_inner2"><div class="sub_inner"></div></div>'+
        '<style>'+
        '#bidc_panel { position: fixed; z-index: 4000; top: 60px; left: calc(50% - 300px); '+
        'font: bold 16px/24px Meiryo; color: #666; background: #fff; '+
        'width: 620px; height: auto; padding: 17px 5px 0; text-align: left; '+
        'border: 1px solid #aaa; border-radius: 6px; box-sizing: content-box; '+
        'overflow: hidden; box-shadow: 0 20px 30px rgb(0, 0, 0, .2); } '+
        '.bidc_span { font: bold 18px/16px Meiryo; margin-left: 20px; vertical-align: -1px; } '+
        '.bidc_inner { position: absolute; top: 54px; left: 5px; padding: 11px 15px 0;'+
        'height: 37px; width: 590px; background: #e4eef8; line-height: 30px; } '+
        '.now_item, .delete_item { display: inline-block; width: 40px; color: #008dfe; } '+
        '.execute, .end_task, .bidc_help { font: bold 16px/24px Meiryo; color: inherit; '+
        'padding: 1px 6px; height: 28px; -webkit-appearance: button; cursor: pointer; } '+
        '.execute { position: absolute; top: 11px; right: 20px; } '+
        '.end_task { position: absolute; top: 14px; right: 25px; } '+
        '.bidc_help { position: absolute; top: 14px; right: 125px; } '+
        '.file_read { display: none; } '+
        '.bidc_inner2 { margin-top: 66px; height: 0; } '+
        '.sub_inner { font: normal 16px/26px Meiryo; padding: 20px; color: #000; } '+
        '</style><div>';

    if(!document.querySelector('#bidc_panel')){
        document.querySelector('body').insertAdjacentHTML('beforeend', panel); }

} // panel_disp()



function close_pannel(){
    history.pushState('0', '0', location.href.replace(/\?.*$/, '')); // URLから「?」以降を削除
    let bidc_panel=document.querySelector('#bidc_panel');
    if(bidc_panel){
        bidc_panel.remove(); }}



function read_local(){
    let read_json=localStorage.getItem('iine_id_back'); // ローカルストレージ 保存名
    iine_block_data=JSON.parse(read_json);
    if(iine_block_data==null){
        data_error(); }
    else{
        return true; }}



function data_error(){
    let bidc_inner=document.querySelector('.bidc_inner');
    if(bidc_inner){
        bidc_inner.innerHTML=
            "⛔  ブロックデータがないので処理ができません　このツールを終了してください"; }

    let end_task=document.querySelector('.end_task');
    if(end_task){
        end_task.onclick=function(){
            close_pannel(); }}}



function write_local(){
    let write_json=JSON.stringify(iine_block_data);
    localStorage.setItem('iine_id_back', write_json); } // ローカルストレージ 保存名



function backup(filename){
    let write_json=JSON.stringify(iine_block_data);
    let blob=new Blob([write_json], {type: 'application/json'});
    let a_elem=document.createElement('a');
    a_elem.href=URL.createObjectURL(blob);
    a_elem.download=filename; // 保存ファイル名
    a_elem.click();
    URL.revokeObjectURL(a_elem.href); }



function reg_set(){
    iine_block_id=[];
    iine_block_img=[];
    for(let k=0; k<iine_block_data.length; k++){
        iine_block_id[k]=iine_block_data[k][0];
        iine_block_img[k]=iine_block_data[k][1]; }
    block_filter_id=iine_block_id.join('|');
    block_regex_id=RegExp(block_filter_id);
    block_filter_img=iine_block_img.join('|');
    block_regex_img=RegExp(block_filter_img); }



function read_backup(button, sabun, n){ // sabun:「1」で差分追加
    button.click();

    button.addEventListener("change", function(){
        if(!(button.value)) return; // ファイルが選択されない場合
        let file_list=button.files;
        if(!file_list) return; // ファイルリストが選択されない場合
        let file=file_list[0];
        if(!file) return; // ファイルが無い場合

        let file_reader=new FileReader();
        file_reader.readAsText(file);
        file_reader.onload=function(){
            if(file_reader.result.slice(0, 15)=='[["tmp1","img1"'){ // iine_mute.jsonの確認
                let data_in=JSON.parse(file_reader.result);

                if(sabun==1){ // 差分追加処理
                    for(let k=0; k<data_in.length; k++){
                        if(block_regex_id.test(data_in[k][0])!=true){ // ID未出なら追加
                            iine_block_data.push([data_in[k][0], data_in[k][1]]); }
                        else if(block_regex_id.test(data_in[k][0])==true){ // ID既出の場合
                            for(let s=0; s<iine_block_data.length; s++){
                                if(iine_block_data[s][0]==data_in[k][0]){
                                    if(iine_block_data[s][1]!=data_in[k][1]){ // imgのSRCが異なる
                                        if(Number(iine_block_data[s][1].slice(0, 8))
                                           <Number(data_in[k][1].slice(0, 8))){
                                            iine_block_data[s][1]=data_in[k][1]; }}}}}}}
                else{
                    iine_block_data=data_in; } // 読込み上書き処理

                write_local(); // ローカルストレージ 保存
                reload_q(n);
            }}; });

} //read_backup()



function help(text, n){
    let bidc_help=document.querySelector('.bidc_help');
    let bidc_inner2=document.querySelector('.bidc_inner2');
    let sub_inner=document.querySelector('.sub_inner');
    sub_inner.innerHTML=text;

    if(n==1){
        bidc_inner2.style.height='auto'; } // 初期設定

    bidc_help.onclick=function(){
        if(bidc_inner2.style.height!='auto'){
            bidc_inner2.style.height='auto'; }
        else{
            bidc_inner2.style.height='0px'; }}}
