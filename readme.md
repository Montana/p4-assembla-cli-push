## Instructions 

Make a directory entitled `p4-test` and then have another directory called `main`. In the `main` directory, make a `.travis.yml` file with the following directions:

```yaml
dist: bionic
install: skip
```

Here's some sample environment variables: 

```bash
P4PORT=ssl:p4-us.assembla.com:30920
P4HOST=travis-ci-ext/Travis-CI-P4-and-SVN-demo-space.8
P4CLIENT=montana6
P4USER=MontanaMendy
P4_ssl:p4-us.assembla.com:30920_CHARSET=auto
P4CONFIG=.p4config
```
In `P4CLIENT` put what your workspace name is (can be anything), then run the following: 

```bash
p4 client -S //depot/main -o | p4 client -i
```

The above command will save your `P4CLIENT` setting and then set it, so when you `reconcile` the proper files get pushed to Assembla. Then make sure you go back to your environment variables to make sure they haven't changed: 

```bash
 vim ~/.p4enviro
 ```
 
Then make sure your `p4 info` matches to your environment variables, then run: 

```bash
p4 reconcile
```

Then push up your files: 

```bash
p4 submit -d "import"
```

## Screenshot for a view of the flow

<img width="547" alt="Screen Shot 2022-06-14 at 7 41 05 PM" src="https://user-images.githubusercontent.com/20936398/173725247-b64111ab-30ef-461c-b248-203c4f6249f2.png">


Check back on Assembla and see if your files are there.
