#### 상태
- fresh: 새롭게 추가된 쿼리 & 만료되지 않은 쿼리 -> 컴포넌트 마운트 or 업데이트되도 fetch X
- fetching: 요청 중인 쿼리
- stale: 만료된 쿼리 -> 컴포넌트 마운트 or 업데이트되면 fetch
- inactive: 비활성화된 쿼리 -> 특정 시간 지나면 GC에 의해 제거

#### useQuery
```js
const requestData = useQuery(queryKey, queryFn, options);
```
- queryKey: string | unknown[], 캐싱 처리관련
- queryFn: (context: QueryFunctionContext) => Promise<TData>
- options: useQuery 기능 제어

`queryKey가 다르면 호출하는 api가 같더라도 캐싱을 별도 관리`

#### returns
- data
- isLoading
- isFetching
- isSuccess
- isError
- error

#### options
- cacheTime
- staleTime
- refetchOnMount
- refetchOnWindowFocus
- refetchInterval
- refetchIntervalInBackground
- enabled
- onSuccess
- onError
- select
- retry

#### staleTime vs cacheTime

#### useQueries



