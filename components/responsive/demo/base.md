---
order: 0
title:
  zh-CN: 基本使用
  en-US: Basic Usage
---

## zh-CN

基本使用。

## en-US

Basic Usage

````jsx
import { Responsive } from 'choerodon-ui';

class App extends React.Component {
  handleChange = (items) => {
    console.log('responsive change', items);
  };

  renderResponsive = ([size, color]) => {
    return (
      <div style={{ width: size, height: size, backgroundColor: color }} />
    );
  };

  render() {
    const items = [
      { xs: 100, sm: 150, md: 200, lg: 250, xl: 300, xxl: 350 }, // size
      { xs: 'red', sm: 'green', md: 'blue', lg: 'black', xl: 'yellow', xxl: 'pink' }, // color
    ];
    return (
      <Responsive items={items} onChange={this.handleChange}>
        {this.renderResponsive}
      </Responsive>
    );
  }
}


ReactDOM.render(
  <App />,
  mountNode
);
````
