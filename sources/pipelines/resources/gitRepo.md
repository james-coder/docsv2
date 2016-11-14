page_title: Unified Pipeline Resources
page_description: List of supported resources
page_keywords: Deploy multi containers, microservices, Continuous Integration, Continuous Deployment, CI/CD, testing, automation, pipelines, docker, lxc

# gitRepo

You can use a `gitRepo` resource to connect any source control repository to a job. It is typically used as an optional `IN` for [runSh jobs](../jobs/runSh/).  

Adding this resource type creates a webhook on the source repository pointing to Shippable. Due to this, future commits to the repository will automatically create a new version for this resource with the new commit SHA. This will trigger any job(s) that has this resource as an `IN` as long as automatic trigger isn't explicitly turned off.

You can create this resource by adding it to `shippable.resources.yml`
```
- name: <string>                            	#required
  type: gitRepo                             	#required
  integration: <string>                     	#required
  pointer:
    sourceName: org/repo                  		#required
    branch: <string>                          	#optional
```

* `name` should be an easy to remember text string. This will appear in the visualization of this resource in the SPOG view and the list of resources in the Pipelines `Resources` tab. It is also used to refer to this resource in the jobs yml.  If you have spaces in your name, you'll need to surround the value with quotes, however, as a best practice we recommend not including spaces in your names.

* `type` is always set to 'gitRepo'.

* `integration` should be the name of the integration that connects to the Source Control provider where the repository is located. To learn how to create integrations for a specific Source Control Provider, please select from the list below and read the **Adding an integration** section on that page:

	- [GitHub](../../integrations/scm/github/)
	- [Bitbucket](../../integrations/scm/bitbucket/)
	- [Github Enterprise](../../integrations/scm/githubEnterprise/)
	- [Bitbucket Server (formerly Stash)](../../integrations/scm/bitbucketServer/)
	- [Gitlab/GitlabServer](../../integrations/scm/gitlab/)

* `pointer` section provides information about the repository and branch you want to connect to.
	* `sourceName` is the fully qualified name of the repository in the format **org/repo**
	* `branch` specifies the branch you need. If not specified, it defaults to `master`.
