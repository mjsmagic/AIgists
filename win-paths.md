```
const step2 = step1.replace(/( --config=\$')|(\.mocharc-ci\.json')|( --parallel \$')|('/g, (match) => {
  if (match === ' --config=$\'') return ' --config=$\'';
  if (match === '.mocharc-ci.json\'') return 'c/home/jenkins/agent/workspace/.mocharc-ci.json\'';
  if (match === ' --parallel $\'') return ' --parallel $\'';
  return '/';
});
```
