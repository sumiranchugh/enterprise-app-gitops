apiVersion: tekton.dev/v1beta1
kind: PipelineRun
metadata:
  annotations:
    kubectl.kubernetes.io/last-applied-configuration: >
      {"apiVersion":"tekton.dev/v1beta1","kind":"Pipeline","metadata":{"annotations":{},"labels":{"app.kubernetes.io/instance":"enterprise-app-pipeline"},"name":"enterprise-app-pipeline","namespace":"enterprise-app-dev"},"spec":{"params":[{"default":"image-registry.openshift-image-registry.svc:5000/enterprise-app-dev/enterprise-app","name":"IMAGE_REPO","type":"string"},{"default":"latest","name":"IMAGE_TAG","type":"string"},{"default":"tekton","name":"COMMIT_AUTHOR","type":"string"},{"default":"https://github.com/sumiranchugh/enterprise-app.git","name":"GIT_REPO","type":"string"},{"default":"main","name":"GIT_REVISION","type":"string"}],"tasks":[{"name":"fetch-repository","params":[{"name":"url","value":"$(params.GIT_REPO)"},{"name":"revision","value":"main"},{"name":"subdirectory","value":""},{"name":"deleteExisting","value":"false"}],"taskRef":{"kind":"ClusterTask","name":"git-clone"},"workspaces":[{"name":"output","workspace":"workspace"}]},{"name":"build","params":[{"name":"IMAGE","value":"$(params.IMAGE_REPO):latest"},{"name":"TLSVERIFY","value":"false"}],"runAfter":["fetch-repository"],"taskRef":{"kind":"ClusterTask","name":"s2i-php"},"workspaces":[{"name":"source","workspace":"workspace"}]}],"workspaces":[{"name":"workspace"}]}}
    pipeline.openshift.io/started-by: opentlc-mgr
  deletionTimestamp: '2024-02-14T20:04:58Z'
  resourceVersion: '1411996'
  name: enterprise-app-pipeline-q9a2go
  uid: eeefb3c3-42df-4a8b-9cd5-f3ae1c900011
  deletionGracePeriodSeconds: 0
  creationTimestamp: '2024-02-14T20:04:53Z'
  generation: 2
  managedFields:
    - apiVersion: tekton.dev/v1beta1
      fieldsType: FieldsV1
      fieldsV1:
        'f:metadata':
          'f:annotations':
            .: {}
            'f:pipeline.openshift.io/started-by': {}
          'f:labels':
            .: {}
            'f:app.kubernetes.io/instance': {}
            'f:tekton.dev/pipeline': {}
        'f:spec':
          .: {}
          'f:params': {}
          'f:pipelineRef':
            .: {}
            'f:name': {}
          'f:resources': {}
          'f:status': {}
          'f:workspaces': {}
      manager: Mozilla
      operation: Update
      time: '2024-02-14T20:04:53Z'
    - apiVersion: tekton.dev/v1beta1
      fieldsType: FieldsV1
      fieldsV1:
        'f:metadata':
          'f:annotations':
            'f:kubectl.kubernetes.io/last-applied-configuration': {}
      manager: openshift-pipelines-controller
      operation: Update
      time: '2024-02-14T20:04:53Z'
    - apiVersion: tekton.dev/v1beta1
      fieldsType: FieldsV1
      fieldsV1:
        'f:status':
          .: {}
          'f:conditions': {}
          'f:pipelineSpec':
            .: {}
            'f:params': {}
            'f:tasks': {}
            'f:workspaces': {}
          'f:startTime': {}
          'f:taskRuns':
            .: {}
            'f:enterprise-app-pipeline-q9a2go-fetch-repository-gvzbk':
              .: {}
              'f:pipelineTaskName': {}
              'f:status':
                .: {}
                'f:conditions': {}
                'f:podName': {}
                'f:startTime': {}
                'f:taskSpec':
                  .: {}
                  'f:description': {}
                  'f:params': {}
                  'f:results': {}
                  'f:steps': {}
                  'f:workspaces': {}
      manager: openshift-pipelines-controller
      operation: Update
      subresource: status
      time: '2024-02-14T20:04:53Z'
  namespace: enterprise-app-dev
  finalizers:
    - foregroundDeletion
  labels:
    app.kubernetes.io/instance: enterprise-app-pipeline
    tekton.dev/pipeline: enterprise-app-pipeline
spec:
  params:
    - name: GIT_REPO
      value: 'https://github.com/sumiranchugh/enterprise-app.git'
    - name: GIT_REVISION
      value: main
    - name: IMAGE_REPO
      value: >-
        image-registry.openshift-image-registry.svc:5000/enterprise-app-dev/enterprise-app
    - name: IMAGE_TAG
      value: latest
    - name: COMMIT_AUTHOR
      value: tekton
  pipelineRef:
    name: enterprise-app-pipeline
  serviceAccountName: pipeline
  timeout: 1h0m0s
  workspaces:
    - name: workspace
      persistentVolumeClaim:
        claimName: pvc-workspace
status:
  conditions:
    - lastTransitionTime: '2024-02-14T20:04:53Z'
      message: 'Tasks Completed: 0 (Failed: 0, Cancelled 0), Incomplete: 2, Skipped: 0'
      reason: Running
      status: Unknown
      type: Succeeded
  pipelineSpec:
    params:
      - default: >-
          image-registry.openshift-image-registry.svc:5000/enterprise-app-dev/enterprise-app
        name: IMAGE_REPO
        type: string
      - default: latest
        name: IMAGE_TAG
        type: string
      - default: tekton
        name: COMMIT_AUTHOR
        type: string
      - default: 'https://github.com/sumiranchugh/enterprise-app.git'
        name: GIT_REPO
        type: string
      - default: main
        name: GIT_REVISION
        type: string
    tasks:
      - name: fetch-repository
        params:
          - name: url
            value: $(params.GIT_REPO)
          - name: revision
            value: main
          - name: subdirectory
            value: ''
          - name: deleteExisting
            value: 'false'
          - name: IMAGE_REPO
            value: $(params.IMAGE_REPO)
          - name: GIT_REVISION
            value: $(params.GIT_REVISION)
          - name: IMAGE_TAG
            value: $(params.IMAGE_TAG)
          - name: COMMIT_AUTHOR
            value: $(params.COMMIT_AUTHOR)
          - name: GIT_REPO
            value: $(params.GIT_REPO)
        taskRef:
          kind: ClusterTask
          name: git-clone
        workspaces:
          - name: output
            workspace: workspace
      - name: build
        params:
          - name: IMAGE
            value: '$(params.IMAGE_REPO):latest'
          - name: TLSVERIFY
            value: 'false'
          - name: IMAGE_REPO
            value: $(params.IMAGE_REPO)
          - name: IMAGE_TAG
            value: $(params.IMAGE_TAG)
          - name: COMMIT_AUTHOR
            value: $(params.COMMIT_AUTHOR)
          - name: GIT_REPO
            value: $(params.GIT_REPO)
          - name: GIT_REVISION
            value: $(params.GIT_REVISION)
        runAfter:
          - fetch-repository
        taskRef:
          kind: ClusterTask
          name: s2i-php
        workspaces:
          - name: source
            workspace: workspace
    workspaces:
      - name: workspace
  startTime: '2024-02-14T20:04:53Z'
  taskRuns:
    enterprise-app-pipeline-q9a2go-fetch-repository-gvzbk:
      pipelineTaskName: fetch-repository
      status:
        conditions:
          - lastTransitionTime: '2024-02-14T20:04:54Z'
            message: >-
              pod status "PodScheduled":"False"; message: "0/6 nodes are
              available: 6 pod has unbound immediate PersistentVolumeClaims."
            reason: Pending
            status: Unknown
            type: Succeeded
        podName: enterprise-app-pipeline-q9a2go-fetch-repository-gvzbk-pod-pgczl
        startTime: '2024-02-14T20:04:53Z'
        taskSpec:
          description: >-
            These Tasks are Git tasks to work with repositories used by other
            tasks in your Pipeline.

            The git-clone Task will clone a repo from the provided url into the
            output Workspace. By default the repo will be cloned into the root
            of your Workspace. You can clone into a subdirectory by setting this
            Task's subdirectory param. This Task also supports sparse checkouts.
            To perform a sparse checkout, pass a list of comma separated
            directory patterns to this Task's sparseCheckoutDirectories param.
          params:
            - default: ''
              description: 'Revision to checkout. (branch, tag, sha, ref, etc...)'
              name: revision
              type: string
            - default: ''
              description: Refspec to fetch before checking out revision.
              name: refspec
              type: string
            - default: 'true'
              description: >-
                Set the `http.sslVerify` global git config. Setting this to
                `false` is not advised unless you are sure that you trust your
                git remote.
              name: sslVerify
              type: string
            - default: >-
                registry.redhat.io/openshift-pipelines/pipelines-git-init-rhel8@sha256:158b0fda662e5bc05e2ff46f6864a8620bbb45e1a2388a456de43aad6e72d8f7
              description: The image providing the git-init binary that this Task runs.
              name: gitInitImage
              type: string
            - default: ''
              description: >-
                Subdirectory inside the `output` Workspace to clone the repo
                into.
              name: subdirectory
              type: string
            - default: 'true'
              description: >-
                Clean out the contents of the destination directory if it
                already exists before cloning.
              name: deleteExisting
              type: string
            - default: ''
              description: HTTPS proxy server for SSL requests.
              name: httpsProxy
              type: string
            - default: 'true'
              description: >-
                Log the commands that are executed during `git-clone`'s
                operation.
              name: verbose
              type: string
            - default: 'true'
              description: Initialize and fetch git submodules.
              name: submodules
              type: string
            - default: ''
              description: >-
                Define the directory patterns to match or exclude when
                performing a sparse checkout.
              name: sparseCheckoutDirectories
              type: string
            - description: Repository URL to clone from.
              name: url
              type: string
            - default: '1'
              description: >-
                Perform a shallow clone, fetching only the most recent N
                commits.
              name: depth
              type: string
            - default: ''
              description: HTTP proxy server for non-SSL requests.
              name: httpProxy
              type: string
            - default: ''
              description: Opt out of proxying HTTP/HTTPS requests.
              name: noProxy
              type: string
            - default: /tekton/home
              description: >
                Absolute path to the user's home directory. Set this explicitly
                if you are running the image as a non-root user or have
                overridden

                the gitInitImage param with an image containing custom user
                configuration.
              name: userHome
              type: string
          results:
            - description: The precise commit SHA that was fetched by this Task.
              name: commit
            - description: The precise URL that was fetched by this Task.
              name: url
          steps:
            - env:
                - name: HOME
                  value: $(params.userHome)
                - name: PARAM_URL
                  value: $(params.url)
                - name: PARAM_REVISION
                  value: $(params.revision)
                - name: PARAM_REFSPEC
                  value: $(params.refspec)
                - name: PARAM_SUBMODULES
                  value: $(params.submodules)
                - name: PARAM_DEPTH
                  value: $(params.depth)
                - name: PARAM_SSL_VERIFY
                  value: $(params.sslVerify)
                - name: PARAM_SUBDIRECTORY
                  value: $(params.subdirectory)
                - name: PARAM_DELETE_EXISTING
                  value: $(params.deleteExisting)
                - name: PARAM_HTTP_PROXY
                  value: $(params.httpProxy)
                - name: PARAM_HTTPS_PROXY
                  value: $(params.httpsProxy)
                - name: PARAM_NO_PROXY
                  value: $(params.noProxy)
                - name: PARAM_VERBOSE
                  value: $(params.verbose)
                - name: PARAM_SPARSE_CHECKOUT_DIRECTORIES
                  value: $(params.sparseCheckoutDirectories)
                - name: PARAM_USER_HOME
                  value: $(params.userHome)
                - name: WORKSPACE_OUTPUT_PATH
                  value: $(workspaces.output.path)
                - name: WORKSPACE_SSH_DIRECTORY_BOUND
                  value: $(workspaces.ssh-directory.bound)
                - name: WORKSPACE_SSH_DIRECTORY_PATH
                  value: $(workspaces.ssh-directory.path)
                - name: WORKSPACE_BASIC_AUTH_DIRECTORY_BOUND
                  value: $(workspaces.basic-auth.bound)
                - name: WORKSPACE_BASIC_AUTH_DIRECTORY_PATH
                  value: $(workspaces.basic-auth.path)
              image: $(params.gitInitImage)
              name: clone
              resources: {}
              script: >
                #!/usr/bin/env sh

                set -eu


                if [ "${PARAM_VERBOSE}" = "true" ] ; then
                  set -x
                fi


                if [ "${WORKSPACE_BASIC_AUTH_DIRECTORY_BOUND}" = "true" ] ; then
                  cp "${WORKSPACE_BASIC_AUTH_DIRECTORY_PATH}/.git-credentials" "${PARAM_USER_HOME}/.git-credentials"
                  cp "${WORKSPACE_BASIC_AUTH_DIRECTORY_PATH}/.gitconfig" "${PARAM_USER_HOME}/.gitconfig"
                  chmod 400 "${PARAM_USER_HOME}/.git-credentials"
                  chmod 400 "${PARAM_USER_HOME}/.gitconfig"
                fi


                if [ "${WORKSPACE_SSH_DIRECTORY_BOUND}" = "true" ] ; then
                  cp -R "${WORKSPACE_SSH_DIRECTORY_PATH}" "${PARAM_USER_HOME}"/.ssh
                  chmod 700 "${PARAM_USER_HOME}"/.ssh
                  chmod -R 400 "${PARAM_USER_HOME}"/.ssh/*
                fi


                CHECKOUT_DIR="${WORKSPACE_OUTPUT_PATH}/${PARAM_SUBDIRECTORY}"


                cleandir() {
                  # Delete any existing contents of the repo directory if it exists.
                  #
                  # We don't just "rm -rf ${CHECKOUT_DIR}" because ${CHECKOUT_DIR} might be "/"
                  # or the root of a mounted volume.
                  if [ -d "${CHECKOUT_DIR}" ] ; then
                    # Delete non-hidden files and directories
                    rm -rf "${CHECKOUT_DIR:?}"/*
                    # Delete files and directories starting with . but excluding ..
                    rm -rf "${CHECKOUT_DIR}"/.[!.]*
                    # Delete files and directories starting with .. plus any other character
                    rm -rf "${CHECKOUT_DIR}"/..?*
                  fi
                }


                if [ "${PARAM_DELETE_EXISTING}" = "true" ] ; then
                  cleandir
                fi


                test -z "${PARAM_HTTP_PROXY}" || export
                HTTP_PROXY="${PARAM_HTTP_PROXY}"

                test -z "${PARAM_HTTPS_PROXY}" || export
                HTTPS_PROXY="${PARAM_HTTPS_PROXY}"

                test -z "${PARAM_NO_PROXY}" || export
                NO_PROXY="${PARAM_NO_PROXY}"


                /ko-app/git-init \
                  -url="${PARAM_URL}" \
                  -revision="${PARAM_REVISION}" \
                  -refspec="${PARAM_REFSPEC}" \
                  -path="${CHECKOUT_DIR}" \
                  -sslVerify="${PARAM_SSL_VERIFY}" \
                  -submodules="${PARAM_SUBMODULES}" \
                  -depth="${PARAM_DEPTH}" \
                  -sparseCheckoutDirectories="${PARAM_SPARSE_CHECKOUT_DIRECTORIES}"
                cd "${CHECKOUT_DIR}"

                RESULT_SHA="$(git rev-parse HEAD)"

                EXIT_CODE="$?"

                if [ "${EXIT_CODE}" != 0 ] ; then
                  exit "${EXIT_CODE}"
                fi

                printf "%s" "${RESULT_SHA}" > "$(results.commit.path)"

                printf "%s" "${PARAM_URL}" > "$(results.url.path)"
          workspaces:
            - description: >-
                The git repo will be cloned onto the volume backing this
                Workspace.
              name: output
            - description: >
                A .ssh directory with private key, known_hosts, config, etc.
                Copied to

                the user's home before git commands are executed. Used to
                authenticate

                with the git remote when performing the clone. Binding a Secret
                to this

                Workspace is strongly recommended over other volume types.
              name: ssh-directory
              optional: true
            - description: >
                A Workspace containing a .gitconfig and .git-credentials file.
                These

                will be copied to the user's home before any git commands are
                run. Any

                other files in this Workspace are ignored. It is strongly
                recommended

                to use ssh-directory over basic-auth whenever possible and to
                bind a

                Secret to this Workspace over other volume types.
              name: basic-auth
              optional: true
