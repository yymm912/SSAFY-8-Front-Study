# Reflow
생성된 DOM 노드의 레이아웃 수치(너비, 높이, 위치) 변경 시 영향 받은 모든 노드의(자신, 자식, 부모, 조상) **모든 노드의 수치**를 다시 계산하여, 렌더 트리를 재생성하는 과정이며 또한, ```Reflow``` 과정이 끝난 후 재생성된 트리는 다시 그리게 되는데 이 과정을 ```Repaint```라 부름.

```js
function reFlow(){
    document.querySelector('#container').style.width="600px"
    return false;
}

```

# Repaint
Reflow 발생 이유와 같이 스타일의 모든 변경이 레이아웃 수치에 영향을 받는것은 아님.
노드의 ```background-color, visibility, outline``` 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않으므로 Reflow 과정이 생략된 Repaint과정만 일어나게 됨.

```js
function rePaint(){
    document.querySelector("#container").style.backgroundColor="red"
    return false;
}

```