# Landing Pages

Testing OpenShift s2i utility - dummy repo for different lighttpd configuration landing pages to feed to a s2i builder image.

### CLI Info for Testing

To build I am using the builder image not available publically yet (will put link here when available).

Compile the builder image as per the instructions then use [OpenShift's s2i](https://github.com/openshift/source-to-image) utility to create the images from the builder image by specifying the path with `--context-dir=` option:

```bash
s2i build https://github.com/kierk/landing-pages.git --context-dir=validation/ lighttpd-centos7 validation-landing
```

Where the `--context-dir` option is the path in this repo to the root dir for the application source, `lighttpd-centos7` is the name of the builder image in your local repository, and `validation-landing` is the name of the image to be created by the builder.

Finally to run the newly created image execute:

```bash
docker run -i -p <host-port>:8080 <name-of-image-created-above>
```