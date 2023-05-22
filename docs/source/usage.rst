Usage
=====

The application is running on: https://thinkreal-ec2.cskorski.com/login

However it has some errors and it is advised to run it via Docker. Each service has a repository on Docker Hub.

To update the deployed repositories, follow these steps within each service:

.. code-block::

  docker build -t <image_name>

.. code-block::

  docker tag <image_name>:<version> <repro_name>/<image_name>:<version>
  
.. code-block::

  docker push <repro_name>/<image_name>:<version>

|
|

To build, run in develop mode, or in production follow the detailed constructions in the README of the corresponding repository:

| `Frontend <https://github.com/Advanced-SE-2023/frontend/blob/main/README.md>`_
| `Backend <https://github.com/Advanced-SE-2023/backend/blob/main/README.md>`_
