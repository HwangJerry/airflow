 .. Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

 ..   http://www.apache.org/licenses/LICENSE-2.0

 .. Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.

Google Cloud Composer Operators
===============================

Cloud Composer is a fully managed workflow orchestration service, enabling you to create, schedule, monitor,
and manage workflows that span across clouds and on-premises data centers.

Cloud Composer is built on the popular Apache Airflow open source project and operates using the
Python programming language.

By using Cloud Composer instead of a local instance of Apache Airflow, you can benefit from the best of
Airflow with no installation or management overhead. Cloud Composer helps you create Airflow
environments quickly and use Airflow-native tools, such as the powerful Airflow web interface and
command-line tools, so you can focus on your workflows and not your infrastructure.

For more information about the service visit `Cloud Composer production documentation <Product documentation <https://cloud.google.com/composer/docs/concepts/overview>`__

Create an environment
---------------------

Before you create a cloud composer environment you need to define it.
For more information about the available fields to pass when creating an environment, visit `Cloud Composer create environment API. <https://cloud.google.com/composer/docs/reference/rest/v1/projects.locations.environments#Environment>`__

A simple environment configuration can look as followed:

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 0
    :start-after: [START howto_operator_composer_simple_environment]
    :end-before: [END howto_operator_composer_simple_environment]

With this configuration we can create the environment:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerCreateEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_create_composer_environment]
    :end-before: [END howto_operator_create_composer_environment]

or you can define the same operator in the deferrable mode:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerCreateEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_create_composer_environment_deferrable_mode]
    :end-before: [END howto_operator_create_composer_environment_deferrable_mode]

Get an environment
------------------

To get an environment you can use:

:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerGetEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_get_composer_environment]
    :end-before: [END howto_operator_get_composer_environment]

List environments
--------------------

To get an environment you can use:

:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerListEnvironmentsOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_list_composer_environments]
    :end-before: [END howto_operator_list_composer_environments]

Update environments
----------------------

You can update the environments by providing an environment config and an updateMask.
In the updateMask argument you specify the path, relative to the environment, of the field to update.
For more information on updateMask and other parameters take a look at `Cloud Composer update environment API. <https://cloud.google.com/composer/docs/reference/rest/v1/projects.locations.environments/patch>`__

An example of a new service config and the updateMask:

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 0
    :start-after: [START howto_operator_composer_update_environment]
    :end-before: [END howto_operator_composer_update_environment]

To update a service you can use:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerUpdateEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_update_composer_environment]
    :end-before: [END howto_operator_update_composer_environment]

or you can define the same operator in the deferrable mode:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerCreateEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_update_composer_environment_deferrable_mode]
    :end-before: [END howto_operator_update_composer_environment_deferrable_mode]

Delete a service
-----------------

To delete a service you can use:

:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerDeleteEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_delete_composer_environment]
    :end-before: [END howto_operator_delete_composer_environment]

or you can define the same operator in the deferrable mode:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerDeleteEnvironmentOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_delete_composer_environment_deferrable_mode]
    :end-before: [END howto_operator_delete_composer_environment_deferrable_mode]


List of Composer Images
------------------------

You can also list all supported Cloud Composer images:

:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerListImageVersionsOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_composer_image_list]
    :end-before: [END howto_operator_composer_image_list]

Run Airflow CLI commands
------------------------

You can run Airflow CLI commands in your environments, use:
:class:`~airflow.providers.google.cloud.operators.cloud_composer.CloudComposerRunAirflowCLICommandOperator`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_run_airflow_cli_command]
    :end-before: [END howto_operator_run_airflow_cli_command]

or you can define the same operator in the deferrable mode:

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_operator_run_airflow_cli_command_deferrable_mode]
    :end-before: [END howto_operator_run_airflow_cli_command_deferrable_mode]

Check if a DAG run has completed
--------------------------------

You can use sensor that checks if a DAG run has completed in your environments, use:
:class:`~airflow.providers.google.cloud.sensors.cloud_composer.CloudComposerDAGRunSensor`

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_sensor_dag_run]
    :end-before: [END howto_sensor_dag_run]

or you can define the same sensor in the deferrable mode:

.. exampleinclude:: /../../google/tests/system/google/cloud/composer/example_cloud_composer.py
    :language: python
    :dedent: 4
    :start-after: [START howto_sensor_dag_run_deferrable_mode]
    :end-before: [END howto_sensor_dag_run_deferrable_mode]
