# 页面布局

- 水平垂直居中

```css

    /* transform + position */
    .wrapper{
        position: relative;
    }
    .content{
        position: absolute;
        width: 100px;
        height: 100px;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
    }

    /* flex */
    .wrapper{
        display: flex;
        align-items: center;
        justify-content: center;
        height: 100vh;
        width: 100%;
    }
    .content{
        width: 100px;
        height: 100px;
    }

    /* margin + position */
    .wrapper{
        position: relative;
    }
    .content{
        width: 100px;
        height: 100px;
        position: absolute;
        top: 50%;
        left: 50%;
        margin-top: -50px;
        margin-left: -50px;
    }

    /* table-cell  */
    .wrapper{
        display: table-cell;
        width: 100vw;
        text-align:center;
    }

    .content{
        width: 100px;
        height:100px;
        display: inline-block;
    }

    ...

```

![center](../assets/center.png)



- 多列布局

