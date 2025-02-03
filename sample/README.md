# Terraform Workflow Guide

## Introduction

This document provides a step-by-step guide on how to execute Terraform commands for managing infrastructure across different environments. Each environment has a dedicated folder, and Terraform commands must be run from the respective environment directory.

## Terraform Workflow

### **Initialize Terraform** (`init`)

Before executing any Terraform commands, you need to initialize the working directory.

### **Command:**

```bash
cd environments/<environment-name>
make init

```

### **Example:**

```bash
cd environments/prod-eu
make init

```

This will download all required providers and modules, setting up the working directory for Terraform.

---

### **Plan Changes** (`plan`)

Before applying changes, you should generate an execution plan to see what Terraform will modify.

### **Command:**

```bash
cd environments/<environment-name>
make plan

```

### **Example:**

```bash
cd environments/prod-eu
make plan

```

This command will show what resources will be created, updated, or destroyed.

> Tip: Ensure all changes in main.tf and .tfvars are committed before running the plan.
> 

---

### **Validate Configuration** (`validate`)

To check whether the current Terraform configuration is valid and does not contain errors, run:

### **Command:**

```bash
cd environments/<environment-name>
make validate

```

### **Example:**

```bash
cd environments/prod-eu
make validate

```

This will check for syntax errors, missing variables, and general configuration validity.

---

### **Apply Changes** (`apply`)

Once you are satisfied with the Terraform plan, apply the changes to provision infrastructure.

### **Command:**

```bash
cd environments/<environment-name>
make apply

```

### **Example:**

```bash
cd environments/prod-eu
make apply

```

This command will **create/update** resources in AWS as per your Terraform configuration.

> Warning: Double-check the plan before running apply, as this will make real changes in the infrastructure.
> 

---

## Additional Terraform Commands

### **Destroy Infrastructure** (`destroy`)

To remove all infrastructure related to an environment, run:

### **Command:**

```bash
cd environments/<environment-name>
make destroy

```

### **Example:**

```bash
cd environments/prod-eu
make destroy

```

This will **permanently delete** all resources in the environment. Use with caution.

---
