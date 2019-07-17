## Utils

- excel导出

```js
    function exportExcel(title, dataSource = [], exportKeys = {}){
        let headerItem = '';
        let rows = '';
        const keys = Object.keys(exportKeys);
        const theaders = keys.map(k => exportKeys[k]);
        theaders.forEach((el)=>{
            headerItem+=`<th>${el}</th>`;
        });
        dataSource.forEach(el=>{
            let tds = '';
            keys.forEach(key=>{
                tds += `<td>${el[key]}</td>`
            })
            rows += `<tr>${tds}</tr>`
        })
        const excelHtml = `
            <html>
                <head>
                    <meta charset='utf-8' />
                    <style>
                        .tableA {
                            border-collapse: collapse;
                        }
                        .tableA .title th{
                            height: 50px;
                            font-size: 24px;
                            font-family: '微软雅黑';
                            font-weight: 700;
                        }
                        .tableA tr th {
                            border: 1px #000 solid;
                            height: 40px;
                            background: #efefef;
                        }
                        .tableA tr td {
                            padding: 0 40px;
                            border: 1px #000 solid;
                            height: 40px;
                            text-align: center;
                        }
                    </style>
                </head>
                <body>
                    <table bordercolor="black" class="tableA">
                        <tr class="title">
                            <th colspan=${keys.length+1} align="left">${title}</th>
                        </tr>
                        <tr>
                            ${headerItem}
                        </tr>
                        ${rows}
                    </table>
                </body>
            </html>
        `;
        const excelBlob = new Blob([excelHtml], {type: 'application/vnd.ms-excel'});
        // 创建一个a标签
        const oA = document.createElement('a');
        // 利用URL.createObjectURL()方法为a元素生成blob URL
        oA.href = URL.createObjectURL(excelBlob);
        // 给文件命名
        oA.download = `${title}.xls`;
        // 模拟点击
        oA.click();
    }

```