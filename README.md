# Learn How to DLL Plugin work in webpack
Link from LogRocket Blog: https://blog.logrocket.com/speed-up-your-webpack-build-with-the-dll-plugin

## About Dll Plugin
Link from webpack: https://webpack.js.org/plugins/dll-plugin

> The DllPlugin and DllReferencePlugin provide means to split bundles in a way that can drastically improve build time performance. The term "DLL" stands for Dynamic-link library which was originally introduced by Microsoft.

## How to run
First: yarn buildVendor
Then: yarn build

Testing the bundles using the `speed-measure-webpack-plugin` gives the following benchmarks:

```
Specs: i5-6200U 8gb ram windows 10

With DllPlugin (Average 3 builds)
Building vendor bundle:
*3370ms

Building main bundle:
146.6ms

Without DllPlugin (Average 3 builds)
Building vendor bundle:
3312ms

Building main bundle:
3583.6ms

Assuming you only build the vendor bundle at the beginning of a coding session, and you reload say a hundred times in a session, here’s the total time you’ll spend waiting:

With DllPlugin
3370+(146.6*100) = 18030ms

Without DllPlugin
3312+(3583.6*100) = 361672ms

That’s a 95% decrease of build time! Makes for incredible productivity gains.
```

## Conclusion
This optimization doesn’t in any way apply to your production build. It only caches the specified bundles to speed up development builds.
