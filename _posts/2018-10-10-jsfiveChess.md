---
layout: post
title: js实现五子棋
date: 2018-10-10
tags: javascript
---

### 1.实现思路

​	使用canvas绘制棋盘，绑定棋盘点击事件，根据点击的坐标来确定落子位置，在相应位置绘制棋子，实现“落子”，每次落子后进行胜负判定，定出胜负则弹出相应的提示信息。

### 2.js具体实现

#### （1）相关变量初始化

```javascript
const chess = document.getElementById('chess-board');
const context = chess.getContext('2d');
//当前执子是否是黑子
let isBlack = true;
//棋盘落子情况
let chessBox = [];

//初始化棋盘18*18
for(let i = 0; i < 19 ; i++){
    chessBox[i] = [];
    //未落子为0，落黑子为1，落白子为2
    for(let j = 0;j < 19 ; j++){
        chessBox[i][j] = 0;
    }
}
```

#### (2)绘制棋盘函数

```javascript
//绘制棋盘
function paintBoard(){
    for(let i = 0;i < 19;i++){
        context.strokeStyle = '#000';
        context.moveTo(40+i*40,40);
        context.lineTo(40+i*40,760);
        context.stroke();
        context.moveTo(40,40+i*40);
        context.lineTo(760,40+i*40);
        context.stroke();
    }
}
```

#### (3)绘制棋子函数,落子后进行判定

```javascript
//落子,i,j为行列来确定落子点，k表示黑白子
function drawChess(i,j,k,judge){
    context.beginPath();
    context.arc(40+i*40,40+j*40,17,0,Math.PI*2);
    let gradient = context.createRadialGradient(40+i*40,40+j*40,17,40+i*40,40+j*40,0);
    if(k){
        gradient.addColorStop(0,'#0a0a0a');
        gradient.addColorStop(1,'#646766');
    }else{
        gradient.addColorStop(0,'#d1d1d1');
        gradient.addColorStop(1,'#f9f9f9');
    }
    context.fillStyle = gradient;
    context.fill();
    context.closePath();
    judge(i,j,k);
}
```

#### (4)胜负判定函数

```javascript
//判断谁获胜了i,j为行列来确定落子点，k表示黑白子
function isGameOver(i,j,k){
    console.log(i,j);
    let count = 1;
    let player = k ? 1 : 2;
    // 判断上下是否五子
    for(let ii = i + 1;ii < 19; ii++){
        if(chessBox[ii][j]==player){
            count++;
        }else{
            break;
        }
        
    }
    for(let ii = i-1;ii > -1 ;ii--){
        if(chessBox[ii][j]==player){
            count++;
        }else{
            break;
        }
        
    }
    checkFive(count,k);
   
    //判断左右是否五子
    count=1;
    for(let jj = j+1; jj < 19;jj++){
        if(chessBox[i][jj]==player){
            count++;
        }else{
            break;
        }
    }
    for(let jj = j-1; jj > -1;jj--){
        if(chessBox[i][jj]==player){
            count++;
        }else{
            break;
        }
    }
    checkFive(count,k);
    //判断左上到右下是否五子
    count=1;
    for(let ii=i+1,jj=j+1;ii<19&&jj<19;ii++,jj++){
        if(chessBox[ii][jj]==player){
            count++;
        }else{
            break;
        }
    }
    for(let ii=i-1,jj=j-1;ii>-1&&jj>-1;ii--,jj--){
        if(chessBox[ii][jj]==player){
            count++;
        }else{
            break;
        }
    }
    checkFive(count,k);

  //  判断左下到右上是否五子
    count=1;
    for(let ii=i-1,jj=j+1;ii>-1&&jj<19;ii--,jj++){
        if(chessBox[ii][jj]==player){
            count++;
        }else{
            break;
        }
    }
    for(let ii=i+1,jj=j-1;ii<19&&jj>-1;ii++,jj--){
        if(chessBox[ii][jj]==player){
            count++;
        }else{
            break;
        }
    }
    checkFive(count,k);
}

function checkFive(count,k){
    if(count>=5){
           // alert('winner is ' + (k?'black':'white'));
        context.font = 'bold 38px Arial';
        context.fillStyle = '#007acc';
        context.textAlign = 'center';
        context.textBaseline = 'middle';
        context.fillText((k?'黑':'白')+'棋获胜！！！',250,250);
        chess.onclick=null;
        return;
    }
}
```

#### (5)棋盘点击事件

```javascript
chess.onclick = function(e){
    // 获取点击坐标
    let x = e.offsetX-15;
    let y = e.offsetY-15;

    //将坐标转化成具体行列数，
    let i = Math.floor(x/40);
    let j = Math.floor(y/40);

    if(chessBox[i][j] == 0){
        drawChess(i,j,isBlack,isGameOver);
        if(isBlack){
            chessBox[i][j] = 1;
        }else{
            chessBox[i][j] = 2;
        }
        isBlack = !isBlack;
    }
}
```

### 3.运行效果

​	在页面加载时调用paintBoard（）函数即可，效果如下图。

![1539180593082](https://raw.githubusercontent.com/gengcongfang/gengcongfang.github.io/master/_posts/img/fivechess-1.png)

![1539180593082](https://raw.githubusercontent.com/gengcongfang/gengcongfang.github.io/master/_posts/img/fivechess-2.png)

