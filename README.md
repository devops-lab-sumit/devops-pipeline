# devops-pipeline
CI/CD + Terraform + EKS practice


 steps:
            - name: checkout code
              uses: actions/checkout@v4

#  What This step Does
# ---------
# When pipeline runs:
# Your repo code will be downloaded into runner
# Location:
# _work/<repo-name>/
# Keyword in GitHub Actions
# Means:
# “Use an existing action instead of writing commands”
# actions/checkout
# This is a pre-built action provided by GitHub
# It does:
# Clone your repository into the runner
# @v4
# Version of the action
# Like:
# software version
# ensures stability
# v4 = latest stable version
# What actions/checkout@v4 Does
# When this runs:
# uses: actions/checkout@v4
# It performs:
# Equivalent of:
# git clone <your-repo>
# BUT:
# Managed internally
# Optimized
# Uses GitHub token automatically
# You CAN Check It Locally

# Since your runner is on your laptop:

# Go to:

# C:\Users\hp\actions-runner\_work\
# What You Should See

# After pipeline runs:

# _work/
#   devops-pipeline/
#     devops-pipeline/
#       README.md
#       .github/
#       docs/
#  Important Behavior
# Each run:
# Reuses workspace (by default)
# Updates code (not always fresh clone)
#  Advanced Insight (Very Important)

# Sometimes GitHub does:

# Clean workspace
# Fetch latest changes instead of full clone

# That’s why it's faster than normal git clone

#  Key Learning
# Concept	Meaning
# Runner	Execution machine
# _work	Workspace root
# Checkout	Pull repo into workspace
# Steps	Run inside repo directory
