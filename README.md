Module Scripts Tree Test Case

This test case exposes performance bottlenecks in the Chrome and Firefox module script loading pipelines.

This is an extracted test case from the Babel code tree consisting of just 170 modules, with some circular references, that seems to result in a large amount of unnecessary processing work during the dependency analysis.

### Results

In Safari, the page loads in 139ms, and displays the error that the export binding does not exist, which is the correct error.

In Chrome 61.0.3154.0, the page loads in 17 seconds, and does not display the correct error message for the missing binding.

In Firefox, the page load takes 10 seconds. On a larger unreduced test case of this tree, the Firefox devtools were likely to crash while inspecting the slowdown.

I haven't been able to test IE yet, but am planning to soon.