> ## Documentation Index
> Fetch the complete documentation index at: https://docs.blitzy.com/llms.txt
> Use this file to discover all available pages before exploring further.

# Environment Testing

> Validate your runtime environment before code generation using the Test Setup button

The **Test Setup** button validates that Blitzy can build and run your application before you start generating code. It lives in the environment setup section of Phase 1 (Codebase Context) on the Blitzy Platform.

> [!NOTE]
>
> **Jump to:** [How It Works](#how-it-works) | [Expected Response Time](#expected-response-time) | [Reading the Results](#reading-the-results) | [When to Retest](#when-to-retest)

## Why Test Your Environment

A validated environment directly improves code generation quality. When Blitzy can compile, run, and test your codebase, it catches its own errors in a validation loop before creating pull requests. Without a passing environment test, Blitzy falls back to static analysis only - meaning issues that a build or test run would catch surface during your review instead.

## How It Works

Clicking **Test Setup** triggers a full validation cycle:

**1. Provision**

Blitzy spins up a clean environment matching your configuration (OS, toolchain, runtime versions).

**2. Clone**

Your connected repository is cloned into the environment.

**3. Execute Setup Instructions**

Your natural-language setup instructions are interpreted and executed step by step - installing dependencies, configuring variables, and running build commands.

**4. Build and Run**

Blitzy attempts to compile the application, run it, and execute any test commands defined in your instructions.

**5. Report**

A pass/fail status is returned with detailed logs for each stage.

## Expected Response Time

Environment tests typically complete in **15-45 minutes** depending on build complexity. Simpler projects with fewer dependencies land closer to 15 minutes, while larger codebases with extensive dependency installation, database migrations, or multi-service startup sequences run closer to 45 minutes.

## Reading the Results

> **All checks pass**
>
> Your environment is correctly configured. Blitzy can build and run your application, which enables the full validation loop during code generation. No action is needed.

> **Partial failure**
>
> Review the logs to identify which step failed. Common causes:
>
> * **Missing environment variables** - A required variable or secret is not defined. Add it in [Environment Configuration](environment_config.md#variables--secrets).
> * **Incorrect toolchain version** - The runtime or build tool version does not match what your codebase requires. Update the version in your setup instructions.
> * **Inaccessible private registry** - Authentication to an internal package registry failed. Verify credentials and registry URLs in your environment secrets.
> * **Build command failure** - A dependency install or compile step errored. Check that your setup instructions match what works on a clean machine.
>
> Fix the failing configuration and click **Test Setup** again.

> **Complete failure**
>
> The environment could not be provisioned or the setup instructions could not be interpreted. Verify that:
>
> * Instructions follow the [natural-language format](environment_config.md#example-setup-instructions) Blitzy expects
> * All required variables and secrets are defined
> * Connected repositories are accessible with the configured permissions
> * The target OS matches your application's requirements

## When to Retest

Rerun **Test Setup** any time you change the underlying configuration:

* Update setup instructions or build commands
* Add, change, or remove environment variables or secrets
* Connect additional repositories or modify repository access
* Change toolchain versions or dependency configurations

> [!TIP]
>
> Treat the environment test as a gate before starting a project. A passing test means Blitzy can iterate on its own output during generation - compiling, testing, and self-correcting before you ever see a pull request.

## Related Guides

> **[Environment Configuration](environment_config.md)**
>
> Configure build instructions, secrets, and private registries

> **[Preparing Your Codebase](preparing_your_codebase.md)**
>
> Repository structure and environment access levels


This documentation is built and hosted on [Mintlify](https://mintlify.com), a developer documentation platform.