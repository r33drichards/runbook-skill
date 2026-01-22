# Example: Update Static Website Content

## Overview
Deploy new content to the production static website and verify successful update.

## Requirements
- **Permissions**: Write access to content bucket, deploy role
- **Tools**: AWS CLI configured, content validation script
- **Network**: VPN connected to production network

## Constraints
- **Maintenance windows**: Any time (no downtime deployment)
- **Impacted resources**: CDN cache, website content
- **Conflicts**: Other content deployments in progress

## Procedure

### Step 1: Stage content
**Action**: Upload new content to staging bucket
```bash
aws s3 sync ./new-content s3://website-staging/
```
**Expected outcome**: Upload completes with no errors
**If failed**: Check AWS credentials and bucket permissions

### Step 2: Validate staged content
**Action**: Run content validation script
```bash
./scripts/validate-content.sh --bucket website-staging
```
**Expected outcome**: Validation passes with exit code 0
**If failed**: Review validation errors, fix content, return to Step 1

### Step 3: Deploy to production
**Action**: Sync staging to production bucket
```bash
aws s3 sync s3://website-staging/ s3://website-production/
```
**Expected outcome**: Sync completes successfully
**If failed**: Proceed to Rollback section

### Step 4: Invalidate CDN cache
**Action**: Create CloudFront invalidation
```bash
aws cloudfront create-invalidation --distribution-id $CDN_ID --paths "/*"
```
**Expected outcome**: Invalidation ID returned
**If failed**: Cache will expire naturally; note in incident log

## Verification
1. Visit production URL and confirm new content appears
2. Check CDN logs for 200 responses
3. Run smoke test: `./scripts/smoke-test.sh --env production`

## Rollback
```bash
# Restore previous content from backup
aws s3 sync s3://website-backup-$(date -d yesterday +%Y%m%d)/ s3://website-production/
aws cloudfront create-invalidation --distribution-id $CDN_ID --paths "/*"
```
Notify content team of rollback at content-team@company.com.

## Escalation
- **Escalate to**: Platform team (#platform-oncall)
- **Escalate after**: 15 minutes if deployment stuck
- **Decision makers**: Content lead for content issues, Platform lead for infra issues
- **Third-party support**: AWS Support (Enterprise, Case ID required)
