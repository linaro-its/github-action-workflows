# Jekyll website actions

There are three workflows:

* `closerequest.yml`
* `pullrequest.yml`
* `push.yml`

In addition to the workflow files, it is necessary to add one or more files called `.github.env-<branch name>` where the file contains these entries:

* `AWS_STATIC_SITE_PROFILE` - AWS authentication profile used for S3 and CloudFront access
* `AWS_STATIC_SITE_URL` - name of the S3 bucket
* `CF_DIST_ID_STATIC_LO` - CloudFront distribution ID
* `CLOUDFRONT_ADD_SECURITY_HEADERS_ARN` - the ARN for the security headers Lambda
* `JEKYLL_ENV` - production or staging
* `SITE_URL` - the URL for the site

## Close Request

This workflow runs a script on Linaro's action runner server to clean up anything built as a result of the pull request specified in the event data.

## Pull Request

This workflow goes through the steps required for a static website pull request, including testing the built site.

## Push

This workflow builds and deploys the site after a push to the repository.
