# promise-flow

An asynchronous function that can execute a series of callback functions in a method chain.

- [🇰🇷 한국어](./README-ko_KR.md)

## Installation

```
npm install promise-flow
```

## Usage

```typescript
import promiseFlow from 'promise-flow';

promiseFlow(placeId, [getPlaceDetailResult, createAddress], {
  onError: () => {
    return mapErrorHandler(location, ErrorType.network);
  },
  onSuccess: (data) => {
    cache.set(data.place_id, data);
  },
});
```

### Parameters

- startValue: The first value to be promised. If the value is not a function, it will be converted to a promised function using the promisify utility function. **Note:** If you pass a function as the first argument and its return value is not a promise, it will raise an error.
- callbackFns: An array of callback functions to be executed in the then method.
- option (optional): An optional object that can be used to provide onError and onSuccess callback functions.
  - onError: A function that will be triggered when the promise reaches the rejected state.
  - onSuccess: A function that will be triggered when the promise reaches the resolved state. The result of the last promise will be passed as the argument.

### Return Value

A Promise object that resolves to the result of the last promise in the chain.

## License

[MIT](./LICENSE)
