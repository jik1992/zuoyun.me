title: FED Reacts
date: 2020/04/10 01:51:04
categories:

- front-end

tags:

---
Lift Time

![](https://miro.medium.com/max/4532/1*lINPzI9FsJnay2_fm4vmzA.png)

|                           | setState | props |
| ------------------------- | -------- | ----- |
| componentWillReveiceProps |          | 🐶     |
| shouldComponentUpdate     | 🐶        | 🐶     |
| componentWillUpdate       | 🐶        | 🐶     |
| render                    | 🐶        | 🐶     |
| componentDidUpdate        | 🐶        | 🐶     |

```react
import React from 'react';
import ReactDOM from 'react-dom';
import { connect } from 'react-redux';
import styled from 'styled-components';


const ReactionInfoContainer = styled.div`
    width: 95%;
    margin-top: 38px;
    position: absolute;
    bottom: ${props => `${props.bottom}px`};
    height: ${props => `${props.height !== null ? props.height : 'auto'}`} 
`;


export default class xxx extends React.PureComponent<IProps,IStates>{
  constructs(props){
    super(props);
  }
  render():React.ReactNode{
    return (
    			<ReactionInfoContainer
                    height={INFO_CONTAINER_HEIGHT_HIDE}
                    bottom={this.props.isPlayground ? '0' : SCHEME_BOTTOM_BAR}
                >
               
          </ReactionInfoContainer>)
  }
}
```





react-redux

* action
* Statetoprops

```react
interface IDispatchProps {
    userLogout: () => void;
}
interface IStateProps {
    taskInfo?: TaskInfo;
}
    
this.props.taskInfo;    

const mapStateToProps = (state: IStoreState) => {
    const { modalProps } = state.modal;
    const { role } = state.role;
    const { taskInfo } = state.chemiriseTasks;
    return {
        taskInfo,
        modalProps,
        role,
    };
};

function mapDispatchToProps(dispatch: Dispatch): IDispatchProps {
    return {
        userLogout: () => {
            dispatch(userLogout());
        },
    };
}

export default connect(
    mapStateToProps,
    mapDispatchToProps,
)(PageHeaderContainer);
```









https://juejin.im/post/5b6f1800f265da282d45a79a



best practices

* https://reactjs.org/blog/2018/03/27/update-on-async-rendering.html#side-effects-on-props-change
* https://reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html



生命周期使用

```
  getSnapshotBeforeUpdate(prevProps, prevState) {
  
  }
  static getDerivedStateFromProps(props, state) {    
			return {}
  }
  componentDidMount() {}
  componentDidUpdate() {}
  componentWillUnMount() {}
```



