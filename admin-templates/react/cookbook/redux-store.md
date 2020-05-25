# Redux Store

Our templates uses `react-redux` state container as main store with `redux-saga`  upon for easier side effects management.

Detailed Documentation: [https://github.com/reduxjs/react-redux](https://github.com/reduxjs/react-redux) and [https://redux-saga.js.org/](https://redux-saga.js.org/)

Entry point at `src/index.js`:

```javascript
import reducers from 'redux/reducers'
import sagas from 'redux/sagas'

const sagaMiddleware = createSagaMiddleware()
const middlewares = [..., sagaMiddleware]
const store = createStore(reducers(history), compose(applyMiddleware(...middlewares)))
sagaMiddleware.run(sagas)

```

