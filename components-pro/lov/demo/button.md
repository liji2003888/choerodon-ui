---
order: 3
title:
  zh-CN: 按钮
  en-US: Button
---

## zh-CN

按钮。

## en-US

Button.

```jsx
import { DataSet, Lov, Output, Row, Col } from 'choerodon-ui/pro';

function handleDataSetChange({ record, name, value, oldValue }) {
  console.log(
    '[dataset]',
    value,
    '[oldValue]',
    oldValue,
    `[record.get('${name}')]`,
    record.get(name),
  );
}

class App extends React.Component {
  ds = new DataSet({
    autoCreate: true,
    fields: [
      {
        name: 'code',
        type: 'object',
        lovCode: 'LOV_CODE',
        lovPara: { code: '111' },
        required: true,
      },
      {
        name: 'code_string',
        type: 'string',
        lovCode: 'LOV_CODE',
        required: true,
        defaultValue: 'SYS.TIME_ZONE',
      },
      { name: 'code_code', type: 'string', bind: 'code.code' },
      { name: 'code_description', type: 'string', bind: 'code.description' },
    ],
    events: {
      update: handleDataSetChange,
    },
  });

  render() {
    const { ds } = this;
    return (
      <Row gutter={10}>
        <Col span={6}>
          <Lov dataSet={ds} name="code" mode="button" clearButton={false} icon="check">
            请选择
          </Lov>
        </Col>
        <Col span={6}>
          <Output dataSet={ds} name="code_code" />
        </Col>
        <Col span={6}>
          <Output dataSet={ds} name="code_description" />
        </Col>
        <Col span={6}>
          <Lov dataSet={ds} name="code_string" mode="button" placeholder="请选择" />
        </Col>
      </Row>
    );
  }
}

ReactDOM.render(<App />, mountNode);
```
