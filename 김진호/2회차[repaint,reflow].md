# Reflow
생성된 DOM 노드의 레이아웃 **수치(너비, 높이, 위치) 변경** 시 영향 받은 모든 노드의 수치(자신, 자식, 부모, 조상) 를 다시 계산하여, 렌더 트리를 재생성하는 과정이며 또한, ```Reflow``` 과정이 끝난 후 재생성된 트리는 다시 그리게 되는데 이 과정을 ```Repaint```라 부름.

```js
function reFlow(){
    document.querySelector('#container').style.width="600px"
    return false;
}

```

## Reflow 과정이 일어나는 상황
- 노드의 추가 또는 제거시.
- 요소의 위치 변경 시.
- 요소의 크기 변경 시(margin, padding, border ...)
- 폰트 변경과 이미지 크기 변경 시.
- 페이지 초기 렌더링 시.
- 윈도우 리사이징 시.


## Reflow 최적화 방법

1. 클래스 변화에 따른 스타일 변경 시, 최대한 DOM 구조 상 끝단에 위치한 노드에 주어야 함.    
   - 가급적 말단에 위치한 노드 수치 변경 시 리플로우 수행 반경을 전체 노드가 아닌 일부 노드로 제한시킬 수 있음. Reflow 수행 비용을 줄일 수 있다는 말과 같음.     
     

2. 인라인 스타일을 최대한 배제
   - 적용 시 코드 가독성과 Reflow 비용을 줄일 수 있음.

3. 애니메이션이 들어간 노드는 ```position:fixed``` 또는 ```position:absolute```로 지정하여 전체 노드에서 분리 시키도록 함.
   - 전체 노드에 걸쳐 Reflow 비용이 들지 않으며, 해당 노드의 Repaint 비용만 들어가게 됨.




# Repaint
Reflow 발생 이유와 같이 스타일의 모든 변경이 레이아웃 수치에 영향을 받는것은 아님.
노드의 ```background-color, visibility, outline``` 등의 스타일 변경 시에는 레이아웃 수치가 변경되지 않으므로 Reflow 과정이 생략된 Repaint과정만 일어나게 됨.

```js
function rePaint(){
    document.querySelector("#container").style.backgroundColor="red"
    return false;
}

```

