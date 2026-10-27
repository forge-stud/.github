# CODEOWNERS for kosseplus-platform
#
# Defines who reviews changes to each part of this repository.
# The LAST matching rule wins. When a rule lists several owners, approval from ANY one of them is enough.
#
# Requirements: teams listed here must be "Visible" (not Secret) and have Write access to this repository.
# Note: GitHub enforces this file automatically only on the GitHub Team plan. Until then, reviewers follow it manually.

# Default: every change is reviewed by the developer team
*                       @forge-stud/developers

# Deployment and security documentation: developers or Platform-Admin
/docs/deployment/       @forge-stud/developers @forge-stud/platform-admin
/docs/security/         @forge-stud/developers @forge-stud/platform-admin

# Repository governance and automation (workflows, ownership rules): Platform-Admin only
/.github/               @forge-stud/platform-admin
