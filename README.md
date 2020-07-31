### App.js의 다른 버전
이 프로젝트의 /src/App.js

```javascript
import React, { Component } from 'react';
import Axios from 'axios';

class App extends Component {
  state = {
    data: {
      userId: null,
      id: null,
      title: null,
      completed: null,
    },
  };

  onclick = () => {
	const { data } = this.state;
    Axios.get("https://jsonplaceholder.typicode.com/todos/1")
      .then((resp) => {
        this.setState({
          data: { data, ...resp.data },
        });
      });
  };

  render() {
	const { data } = this.state;
    return (
      <div>
        <div>아이디: {data.userId}</div>
        <div>제목: {data.title}</div>
        <hr />
        <h1>클릭하세요.</h1>
        <button onClick={this.onclick}>클릭</button>
      </div>
    );
  }
}

export default App;
```

### onclick 함수 부분만 조금 다른 또다른 버전

```javascript
onclick = async () => {
	const { data } = this.state;

	let resp = await Axios.get("https://jsonplaceholder.typicode.com/todos/1");

	this.setState({
		data: { data, ...resp.data },
	});
};
```

### 자세한 사항은 링크 참조
[네이버 블로그](https://blog.naver.com/misschip/222044390371)
