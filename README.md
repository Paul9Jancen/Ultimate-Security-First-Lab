Ultimate AWS Security-First Lab
Zero-Trust Cloud Architecture (Free Tier, Console-Only)
Project Overview

This project demonstrates a production-grade, zero-trust AWS security architecture built entirely within the AWS Free Tier and configured 100% through the AWS Management Console (browser-only).

The lab focuses on identity-first security, least-privilege access, private networking, full auditability, and real-time security alerting, aligned with real-world cloud security and cloud architect best practices.

Goal: Demonstrate hands-on AWS security engineering skills, not theory.

Core Objectives

Implement Zero-Trust Architecture

Enforce Least-Privilege IAM access

Eliminate public exposure (no SSH, no public IPs)

Enable full audit logging and compliance monitoring

Detect and alert on unauthorized API activity

Remain fully within AWS Free Tier with zero billing risk

Architecture Summary

Security Model: Defense-in-Depth + Zero Trust
Access Model: Identity-based (IAM roles only)
Network Model: Private subnets, no internet exposure
Monitoring Model: Continuous logging with event-driven alerts

AWS Services Used

AWS IAM (Users, Roles, Policies)

Amazon EC2 (private, Session Manager access only)

Amazon RDS (PostgreSQL with IAM authentication)

Amazon S3 (encrypted, versioned storage)

AWS CloudTrail (multi-region audit logs)

AWS Config (continuous compliance monitoring)

Amazon EventBridge (security event routing)

Amazon SNS (real-time alerting)

Security Controls Implemented
1. Root Account Hardening

Multi-factor authentication enabled on root account

Root user restricted to emergency use only

No root access for daily operations

2. Identity and Access Management
IAM Users (Least Privilege)
User	Purpose
EC2-Admin	EC2 administration only
RDS-Admin	RDS management
S3-Admin	S3 administration
Security-Auditor	Read-only security audits

No access keys created

Console-only access

Permissions scoped per service

IAM Roles (Zero Trust)
Role	Trusted Service	Purpose
EC2-Role	EC2	Secure access to S3 and RDS
RDS-Role	Lambda	IAM database authentication
S3-Role	EC2	Restricted S3 bucket access

Temporary credentials only

No hardcoded secrets

Service-to-service authentication enforced

3. Secure Data Storage (Amazon S3)

Bucket: lab-secure-bucket-657429748140

Public access fully blocked

AES-256 encryption at rest

Versioning enabled

ACLs disabled (bucket owner enforced)

4. Zero-Trust Compute (Amazon EC2)

Instance type: t3.micro (Free Tier)

Private subnet only

No public IPv4 address

No SSH keys or key pairs

Access via AWS Systems Manager Session Manager

IAM role attached (EC2-Role)

5. Secure Database (Amazon RDS)

PostgreSQL engine

Instance type: db.t2.micro

Private subnet deployment

Public access disabled

IAM database authentication enabled

Security group restricted to EC2 role only

6. Audit Logging (AWS CloudTrail)

Multi-region trail enabled

Logs all management API calls

Log file integrity validation enabled

Dedicated S3 bucket for logs

7. Continuous Compliance (AWS Config)

Records all supported resource types

Continuous configuration recording

Tracks configuration drift and changes in real time

8. Security Event Detection and Alerting
EventBridge

Rule: UnauthorizedAPICallRule

Source: CloudTrail API events

Condition: Unauthorized API calls

State: Enabled

SNS

Topic: LabAlerts

Used for real-time security notifications

GuardDuty and Security Hub Status

Not enabled due to Free Tier account limitations

Detection coverage replaced by:

CloudTrail

EventBridge

SNS-based alerting

Validation and Testing

Unauthorized IAM actions trigger EventBridge events

All API activity logged in CloudTrail

Configuration changes detected by AWS Config

EC2 access verified using Session Manager only

Public access attempts blocked at multiple layers

Zero-Trust Principles Applied

No implicit trust based on network location

Identity verification for all access

Least-privilege permissions everywhere

Continuous monitoring and alerting

Assume breach model enforced

Documentation Strategy

The project is documented using high-impact verification screenshots only:

Root MFA status

IAM users and roles

IAM role trust relationships

Secure S3 bucket configuration

Private EC2 instance settings

RDS private access configuration

CloudTrail logging status

AWS Config recording status

EventBridge rule and SNS topic

No unnecessary screenshots included.

Final Result

This lab represents a realistic, enterprise-grade AWS security environment suitable for:

Cloud Security Engineer portfolios

Cloud Architect roles

SOC and Blue Team fundamentals

Compliance-focused cloud environments

Built with zero cost, zero shortcuts, and production-level security discipline.

Project Title

Ultimate AWS Security-First Lab: Zero-Trust Cloud Architecture
