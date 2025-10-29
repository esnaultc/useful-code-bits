Short HOW-TO notes
==================

These are not fully described tutorials, but quick notes I take as I go. In
other words, this is what worked on my machine, this might not work for other
setups.

Setting up conda, git and neovim on Windows machine
***************************************************

Working with Terminal in Windows is quite different than Linux or macOS,
the environment variables are handled from the System proterties pannel >
Advanced > Environment variables. This will be useful later to add miniconda
directories to the PATH.

Install miniconda
+++++++++++++++++++

Open the Command prompt exe, install
`miniconda from command line <https://www.anaconda.com/docs/getting-started/miniconda/install#quickstart-install-instructions>`_:

.. code-block:: bash

  curl https://repo.anaconda.com/miniconda/Miniconda3-latest-Windows-x86_64.exe -o .\miniconda.exe
  start /wait "" .\miniconda.exe /S
  del .\miniconda.exe

This installs the applications Anaconda Prompt and Anaconda PowerShell Promt. I will
be using Anaconda PowerShell Prompt for next steps.

Update the PATH so the terminal will find the packages by adding

.. code-block:: bash

  C:\Users\{username}\AppData\Local\miniconda3\Scripts
  C:\Users\{username}\AppData\Local\miniconda3\Library\bin

Install Git and neovim
++++++++++++++++++++++

Open Anaconda PowerShell Prompt, the ``base`` environment should be activated.
install `Git <https://git-scm.com/install/windows>`_ and `neovim <https://blog.nikfp.com/how-to-install-and-set-up-neovim-on-windows>`_:

.. code-block:: bash

  winget install --id Git.Git -e --source winget
  winget install neovim

Using winget because these should be in all environments.

Exit and reopen Anaconda PowerShell Prompt.

Verify the installations by running:

.. code-block:: bash

  conda --version
  git --help
  nvim --version



