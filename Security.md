# Security Policy
 
## Disclaimer
 
These Conditional Access templates are provided as reference implementations and best-practice examples.
 
Organizations must review, test, and adapt all policies according to their own security, compliance, operational, and business requirements before enabling them in production environments.
 
### Recommended Deployment Approach
 
⚠️ **Never deploy Conditional Access policies directly in an enabled (ON) state.**
 
ALSO strongly recommends the following deployment process:
 
1. Deploy all policies in **OFF** mode initially.
2. Review policy scope, assignments, exclusions, and dependencies.
3. Test policies in a dedicated pilot group where applicable.
4. Move policies to **Report-only** mode to observe the expected impact.
5. Validate sign-in logs, reporting data, and user experience.
6. Enable policies only after successful validation and stakeholder approval.
 
Failure to properly test Conditional Access policies may result in:
 
- User lockouts
- Administrative lockouts
- Application access interruptions
- Authentication failures
- Business service disruptions
 
### Shared Responsibility
 
The implementation, validation, and operation of Conditional Access policies remain the sole responsibility of the organization deploying them.
 
ALSO provides these templates to accelerate deployments and align with Microsoft security best practices, but every environment is unique and requires individual assessment before production use.
 
## Liability
 
ALSO assumes no responsibility for:
 
- Service disruptions
- User or administrator lockouts
- Access issues
- Application compatibility problems
- Authentication failures
- Security incidents
- Compliance violations
- Operational impacts
 
resulting from the deployment, modification, or use of these templates.
 
## Reporting Security Issues
 
If you discover a template error, please open an issue.
 
Please do not report sensitive security vulnerabilities publicly.
 
