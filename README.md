<!DOCTYPE html>
<html lang="en">

<head>
    <title>Список задач</title> <!-- Это название страницы, выводится в табе браузера --> 
    <meta charset="utf-8"> 
    <title>Document</title>
    <link rel="stylesheet" href="style.css">
    <script src="java.js"></script>
</head>

<body>
    <input type="text" id="in">
    <button id="add">Добавить</button>
    <hr>
    <div id="out"></div>
</body>
</html>
window.onload = function (){

    var todoList = [];
    if (localStorage.getItem('todo') !=undefined) {
        todoList = JSON.parse(localStorage.getItem('todo'));
        out ();
    }

    document.getElementById ('add') . onclick = function () {
        var d = document.getElementById ('in') .value;
       // {todo : Добавить хлеб, check: false }
       var temp = {};
       temp.todo = d;
       temp.check = false;
       var i = todoList.length;
       todoList [i] = temp;
       console.log (todoList);
       out ();
       localStorage.setItem('todo', JSON.stringify(todoList));
              
    }

    function out (){
        var out = '';
        for (var key in todoList){
            if (todoList[key].check==true) {
                out+= '<input type="checkbox" checked>';
            }
            else{
                out+= '<input type="checkbox">';
            }
            out += todoList [key].todo + '<br>';

        }
        document.getElementById ('out').innerHTML = out ;

    }
}
