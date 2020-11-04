- class -> hooks
- hooks -> class

- PropTypes: 타입 검사  
- useState  
`const [state, setState] = useState(initialState);`
- useCallback: 함수 캐싱  
`const memoizedCallback = useCallback(() => {
    doSomething(a, b);      
 }, [a, b]);`  
- useMemo: 값 캐싱  
`const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);`  
