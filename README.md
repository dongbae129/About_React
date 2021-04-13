# About_React
<h2>목차</h2>
    <ul>
        <li>1.리액트의 이해</li>
        <li>2.라이프 사이클</li>
    </ul>
    <h3>1.리액트의 이해</h3>
    <p>
        리액트는 다른 프레임워크나 라이브러리와 달리 MVC, MVW중 오직 V만 신경 쓰는 라이브러리 입니다.
    </p>
    <p>리액트는 Virtual DOM을 사용합니다. 리액트는 실제 dom에 접근하여 조작하는 대신, 이를 추상화한 자바스크립트 객체를
        구성하여 사용합니다.
    </p>
    <ul>
        <li>1.데이터를 업데이트하면 전체 UI를 VM에 리렌더링합니다</li>
        <li>2.이전 VM에 있던 내용과 현재 내용을 비교합니다</li>
        <li>3.바뀐 부분만 실제 DOM에 적용합니다</li>
    </ul>
    <p>그러면 리액트를 사용하지 않을때 기본적으로 DOM의 작동은 어떻게 일어날까요?</br>
        DOM에 변화가 일어나면 웹브라우저는 css연산, 레이아웃 구성을 하고 페이지를 리페인트 합니다.</br>
        리페인팅을 위해 DOM조작은 필수적이기 때문에 DOM을 최소한으로 조작하는게 필요했습니다.</br>
        그래서 리액트는 VM을 통해 DOM업데이트를 추상화하여 처리횟수를 최소화 하였습니다.
    </p>
    <p>VM 영상 자료 : https://www.youtube.com/watch?v=BYbgopx44vo</p>
    <br>
    <h2>2.라이프 사이클</h2>
    <p>리액트는 life cycle 이라는 생명주기가 있습니다.
     컴포넌트에 따라 마운트, 업데이트, 언마운트 3가지가 존재합니다
    </p>   
     <h4>마운트</h4>
     <p>컴포넌트의 인스턴스가 생성되어 DOM 상에 삽입될때 아래의 순서대로 실행됩니다.</p>
     <ul>
         <li>constructor</li>
         <li>getDerivedStateFromProps</li>
         <li>render</li>
         <li>componentDidMount</li>
     </ul>
     <p><strong>constructor</strong><br>컴포넌트의 생성자 메서드로 컴포넌트를 만들때 처음 실행되며
    초기 state를 정할 수 있습니다</p>
    <p><strong>getDerivedStateFromProps</strong><br>
        getDerivedStateFromProps는 최초 마운트 시와 갱신 시 모두에서 render 메서드를 호출하기 직전에 호출됩니다. state를 갱신하기 위한 객체를 반환하거나, null을 반환하여 아무 것도 갱신하지 않을 수 있습니다.</p>
    <p><strong>render</strong><br>라이프 사이클 메서드 중 유일한 필수 메서드이며 컴포넌트의 모양새를 정의합니다
        this.props와 this.state에 접근할 수 있으며, 리액트 요소를 반환합니다.
    </p>
    <p><strong>componentDidMount</strong>
        <br>컴포넌트가 마운트된 직후, 즉 트리에 삽입된 직후에 호출됩니다. DOM 노드가 있어야 하는 초기화 작업은 이 메서드에서 이루어지면 됩니다. 외부에서 데이터를 불러와야 한다면, 네트워크 요청을 보내기 적절한 위치입니다.
        <br>
        이 메서드는 데이터 구독을 설정하기 좋은 위치입니다. 데이터 구독이 이루어졌다면, componentWillUnmount()에서 구독 해제 작업을 반드시 수행하기 바랍니다.
    </p>
    <hr/>
    <h4>업데이트</h4>
    <p>props, state가 바뀔 때, 부모 컴포넌트가 리렌더링될 때, 강제로 렌더링을 트리거할 때 호출되며 아래의 순서대로 실행됩니다</p>
    <ul>
        <li>static getDerivedStateFromProps</li>
        <li>shouldComponentUpdate</li>
        <li>render</li>
        <li>getSnapshotBeforeUpdate</li>
        <li>componentDidUpdate</li>
    </ul>
    <p><strong>shouldComponentUpdate</strong><br>props 또는 state를 변경했을 때 리렌더링을 시작할지 여부를 결정하는 메서드입니다.
    반드시 true 또는 false를 반환해야 하며 default는 true를 반환합니다.
    잘 사용하지 않으며 성능 최적화를 위하여 사용됩니다.</p>
    <p><strong>getSnapshotBeforeUpdate</strong><br>
        결과물이 브라우저에 실제로 반영되기 직전에 호출됩니다.주로 업데이트하기 직전의 값을 참고할 일이 있을 때 활용됩니다(스크롤 위치)
    </p>
    <p><strong>componentDidUpdate</strong><br>
        갱신이 일어난 직후 호출되며 최초 렌더링에서는 호출되지 않습니다.
    </p>
    <hr/>
    <h4>언마운트</h4>
    <p>컴포넌트를 DOM에서 제거할때 호출됩니다.</p>
    <ul>
        <li>componentWillUnmount</li>
    </ul>    
    <p><strong>componentWillUnmount</strong><br>DOM에서 제거할때 실행되며 didmount에서 등록한 이벤트,타이머, 직접 생성한 DOM이 있다면 여기서 제거 작업을 해야 합니다.</p>
