## Summary 

This is how you get around the CLI for Assembla, specifically when you want to push something to your Assembla repository from the CLI, the Perforce Graphical Version is not the most intuitive, and I just prefer the CLI. So this is tutorial I've just made private for the Travis CI staff. This works a lot like `git` commands, a little more complex - but you'll soon see how.

## Usage

Make a directory entitled `p4-test` and then have another directory called `main`. In the `main` directory, make a `.travis.yml` file with the following directions:

```yaml
language: ruby
   rvm:
    - 2.2
    - jruby
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

## VCS Proxy 

You'll want to make sure your repository is showing up on Travis CI VCS Proxy, it should look like this if you were successful:

<img width="1298" alt="Screen Shot 2022-06-14 at 11 10 35 PM" src="https://user-images.githubusercontent.com/20936398/173755224-e22a9177-d64c-42f1-aeb7-fc4c0739bc10.png">


## Screenshot for a view of the flow

<img width="547" alt="Screen Shot 2022-06-14 at 7 41 05 PM" src="https://user-images.githubusercontent.com/20936398/173725247-b64111ab-30ef-461c-b248-203c4f6249f2.png">

Check back on Assembla and see if your files are there, it should look like this:

<img width="846" alt="Screen Shot 2022-06-14 at 11 06 40 PM" src="https://user-images.githubusercontent.com/20936398/173754520-ba44a32e-bd5b-4845-9a73-ade01f485e0d.png">

You'll see that I pushed successfully, with my Assembla username. You can see my the `.travis.yml` I pushed to Assembla, and ultimately to run on Perforce: 

<img width="661" alt="Screen Shot 2022-06-14 at 11 08 20 PM" src="https://user-images.githubusercontent.com/20936398/173754690-cc112ee0-1ca0-486e-84d8-252eb59acad6.png">
