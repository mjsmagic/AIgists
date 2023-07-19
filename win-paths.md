```
const step2 = step1.replace(/( --config=\$')|(\.mocharc-ci\.json')|( --parallel \$')|('/g, (match) => {
  if (match === ' --config=$\'') return ' --config=$\'';
  if (match === '.mocharc-ci.json\'') return 'c/home/jenkins/agent/workspace/.mocharc-ci.json\'';
  if (match === ' --parallel $\'') return ' --parallel $\'';
  return '/';
});
```


```
const originalCommand = await $`${join('node_modules', 'bin', osExecName('mocha', 'cmd'))} --config=${process.env.WORKSPACE}\\.mocharc-ci.json ${parallel ? '--parallel' : ''} ${test.map(path => join(prefix, path))}`;

// Step 1: Replace double backslashes with forward slashes
const step1 = originalCommand.replace(/\\\\/g, '/');

// Step 2: Replace single quotes around the path with 'c/' prefix
const step2 = step1.replace(/\$'C:/g, "$'c/");

// Step 3: Replace spaces between test paths with single quotes and forward slashes
const step3 = step2.replace(/\s/g, "' $'").replace(/\\/g, '/');
```
