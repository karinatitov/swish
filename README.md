# swish

### Build times improvements:
As for this example i was trying to focus on building ci pipeline of this project, my app is very simple and the build time is quick, but there are a lot of ways we can optimize build times of the applications by utilizing some of the techniques such as:
1. Docker layer caching.
2. External cache sources (using --cache-from command arg. There are some prerequisites to making it work. BuildKit backend is required — this requires Docker version ≥18.09 and setting a DOCKER_BUILDKIT=1 environment variable before invoking docker build. The source image should also be built with --build-arg BUILDKIT_INLINE_CACHE=1 so that it has cache metadata embedded.).
3. Multi-stage builds and virtual environments. Basically we can split the dockerfile int stages and build all the app dependencies and in the second stage build the app using only necessary ones.
4. Also we can use .dockerignore where we can specify all kinds of files. Here is an [example](https://github.com/themattrix/python-pypi-template/blob/master/.dockerignore) of files that could be listed.
I could find more, but think these are the methods that are most common, and that i would try to use first.

###CVEs
1. I generated the report with CVEs listed as a table and saved as an artifact after the ci pipeline is done running. you can find it under the 'Artifacts' section in the Summary of the Action. 
2. In order to remediate all the possible risks, we will have to perform what is called a 'container hardening', and in order to do that i would follow these steps:
  a) Prioritize as per risk level. Key matrices are: 
    CVSS scores 
    Exploit data
    Number of assets reported with the same vulnerability
    Impact of the vulnerability
  b) Timely Remediation.(from my experience, first and most common thing is to find if we can upgrade the package to resolve the issue)
  c) If we want to automate the process, there are tools that have a db with 100s thousands security checks, that ease the overall vulnerability remediation process
  
I believe that the best way of avoiding deploying malicious packages is always run the scan in your ci and catch those vulnerabilities in development process.

  
