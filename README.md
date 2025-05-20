# CF Vite/Miniflare Plugin Workers Analytics Engine Error Reproduction

## Reproduction
`npm run dev`

## Expected
Vite plugin starts worker

## Actual
```
workerd/server/workerd-api.c++:878: error: wrapped binding module can't be resolved (internal modules only); moduleName = analytics-engine:local-simulator

workerd/jsg/util.c++:320: error: e = workerd/server/workerd-api.c++:908: failed: expected !value.IsEmpty(); global did not produce v8::Value
stack: 104596467 10456ed0b 104ab6173 104ab5667 104a9b00b 10453cee7 104543463 104547277 104545a87 1045367e3 10679975f 106799a6f 10679845b 1067981df 10452483b 188ba8273; sentryErrorContext = jsgInternalError; wdErrId = 41fhg41mhf9gesu0liksbgo3
service core:user:cf-vite-wae-reproduction: Uncaught Error: internal error; reference = 41fhg41mhf9gesu0liksbgo3
```

Removing the analytics_engine_datasets binding from wrangler.json causes the worker to start as expected