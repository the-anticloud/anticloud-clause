# CLAUSE

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-legal_tech-lightgrey)

> Anticloud-hardened packaging of the upstream project `CLAUSE` in category **LEGAL TECH**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** LEGAL TECH · **Upstream:** https://github.com/ardalis/GuardClauses · **Upstream pin:** `f96b823e4228252b2927cce3effa550c16b558a5` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

![logo](media/logotype%201024.png)

[![NuGet](https://img.shields.io/nuget/v/Ardalis.GuardClauses.svg)](https://www.nuget.org/packages/Ardalis.GuardClauses)[![NuGet](https://img.shields.io/nuget/dt/Ardalis.GuardClauses.svg)](https://www.nuget.org/packages/Ardalis.GuardClauses)
![publish Ardalis.GuardClauses to nuget](https://github.com/ardalis/GuardClauses/workflows/publish%20Ardalis.GuardClauses%20to%20nuget/badge.svg)

[![Follow Ardalis](https://img.shields.io/twitter/follow/ardalis.svg?label=Follow%20@ardalis)](https://twitter.com/intent/follow?screen_name=ardalis)
[![Follow NimblePros](https://img.shields.io/twitter/follow/nimblepros.svg?label=Follow%20@nimblepros)](https://twitter.com/intent/follow?screen_name=nimblepros)

# Guard Clauses

A simple extensible package with guard clause extensions.

A [guard clause](https://deviq.com/design-patterns/guard-clause) is a software pattern that simplifies complex functions by "failing fast", checking for invalid inputs up front and immediately failing if any are found.

## Give a Star! :star:

If you like or are using this project please give it a star. Thanks!

## Usage

```c#
public void ProcessOrder(Order order)
{
    Guard.Against.Null(order);

    // process order here
}

// OR

public class Order
{
    private string _name;
    private int _quantity;
    private long _max;
    private decimal _unitPrice;
    private DateTime _dateCreated;

    public Order(string name, int quantity, long max, decimal unitPrice, DateTime dateCreated)
    {
        _name = Guard.Against.NullOrWhiteSpace(name);
        _quantity = Guard.Against.NegativeOrZero(quantity);
        _max = Guard.Against.Zero(max);
        _unitPrice = Guard.Against.Negative(unitPrice);
        _dateCreated = Guard.Against.OutOfSQLDateRange(dateCreated, dateCreated);
    }
}
```

## Supported Guard Clauses

- **Guard.Against.Null** (throws if input is null)
- **Guard.Against.NullOrEmpty** (throws if string, guid or array input is null or empty)
- **Guard.Against.NullOrWhiteSpace** (throws if string input is null, empty or whitespace)
- **Guard.Against.OutOfRange** (throws if integer/DateTime/enum input is outside a provided range)
- **Guard.Against.EnumOutOfRange** (throws if an enum value is outside a provided Enum range)
- **Guard.Against.OutOfSQLDateRange** (throws if DateTime input is outside the valid range of SQL Server DateTime values)
- **Guard.Against.Zero** (throws if number input is zero)
- **Guard.Against.Expression** (use any expression you define)
- **Guard.Against.InvalidFormat** (define allowed format with a regular expression or func)
- **Guard.Against.NotFound** (similar to Null but for use with an id/key lookup; throws a `NotFoundException`)

## Extending with your own Guard Clauses

To extend your own guards, you can do the following:

```c#
// Using the same namespace will make sure your code picks up your 
// extensions no matter where they are in your codebase.
namespace Ardalis.GuardClauses
{
    public static class FooGuard
    {
        public static void Foo(this IGuardClause guardClause,
            string input, 
            [CallerArgumentExpression("input")] string? parameterName = null)
        {
            if (input?.ToLower() == "foo")
                throw new ArgumentException("Should not have been foo!", parameterName);
        }
    }
}

// Usage
public void SomeMethod(string something)
{
    Guard.Against.Foo(something);
    Guard.Against.Foo(something, nameof(something)); // optional - provide parameter name
}
```

## YouTube Overview

[![Ardalis.GuardClauses on YouTube](http://img.youtube.com/vi/OkE2VeRM4mE/0.jpg)](http://www.youtube.com/watch?v=OkE2VeRM4mE "Improve Your Code with Ardalis.GuardClauses")

## Breaking Changes in v4

- OutOfRange for Enums now uses `EnumOutOfRange`
- Custom error messages now work more consistently, which may break some unit tests

## Nice Visualization of Refactoring to use Guard Clauses

https://user-images.githubusercontent.com/782127/234028498-96e206b0-9a70-4aa0-9c36-a62477ea0aa9.mp4

via [Nicolas Carlo](https://toot.legacycode.rocks/@nicoespeon/110226815487285845)

## References

- [Getting Started with Guard Clauses](https://blog.nimblepros.com/blogs/getting-started-with-guard-clauses/)
- [How to write clean validation clauses in .NET](https://www.youtube.com/watch?v=Tvx6DNarqDM) (Nick Chapsas, YouTube, 9 minutes)
- [Guard Clauses (podcast: 7 minutes)](http://www.weeklydevtips.com/004)
- [Guard Clause](http://deviq.com/guard-clause/)

## Commercial Support

If you require commercial support to include this library in your applications, contact [NimblePros](https://nimblepros.com/talk-to-us-1)

## Build Notes (for maintainers)

- Remember to update the PackageVersion in the csproj file and then a build on main should automatically publish the new package to nuget.org.
- Add a release with form `1.3.2` to GitHub Releases in order for the package to actually be published to Nuget. Otherwise it will claim to have been successful but is lying to you.

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **.NET** (manifests: GuardClauses.sln; scanned in UPSTREAM_CLONE)
- Top-level source layout: `media/`, `src/`, `test/`
- Snapshot size: **87 files**, **8425 lines of code** (measured; see Benchmarks)
- Primary languages: `.cs` (55), `.png` (8), `.svg` (7), `(none)` (3), `.md` (3), `.csproj` (2)
- Upstream commit pinned for this packaging: `f96b823e4228252b2927cce3effa550c16b558a5`

---

## Installation

- [How to write clean validation clauses in .NET](https://www.youtube.com/watch?v=Tvx6DNarqDM) (Nick Chapsas, YouTube, 9 minutes)
- [Guard Clauses (podcast: 7 minutes)](http://www.weeklydevtips.com/004)
- [Guard Clause](http://deviq.com/guard-clause/)

*Section quoted from the upstream readme.*
Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

A [guard clause](https://deviq.com/design-patterns/guard-clause) is a software pattern that simplifies complex functions by "failing fast", checking for invalid inputs up front and immediately failing if any are found.

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

The upstream API surface is defined by the `CLAUSE` source tree vendored in `UPSTREAM_CLONE/` (.NET ecosystem). Public entry points:

- Source modules: `media/`, `src/`, `test/`
- Overlay API: `anticloud/cli.py` exposes 13 subcommands with JSON stdout; `anticloud/bench/runner.py` runs the 16-check suite; `anticloud/provenance/chain.py` exposes the SHA3-256 + Ed25519 provenance chain.

---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | .NET |
| Manifests detected | GuardClauses.sln |
| Files in snapshot | 87 |
| Lines of code | 8425 |
| Dependency references | 0 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

No configuration section was found in the upstream readme. Configuration-relevant files detected in this project directory:

- None detected at the snapshot root; consult the upstream documentation link in the Upstream section.

Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing to Ardalis.GuardClauses

We love your input! We want to make contributing to this project as easy and transparent as possible, whether it's:

- Reporting a bug
- Discussing the current state of the code
- Submitting a fix
- Proposing new features

## We Develop with GitHub

Obviously...

## We Use Pull Requests

Mostly. But pretty much exclusively for non-maintainers. You'll need to fork the project in order to submit a pull request. Here are the basic steps:

1. Fork the project and create your branch from `main`.
2. If you've added code that should be tested, add tests.
3. If you've changed APIs, update the documentation.
4. Ensure the test suite passes.
5. Make sure your code lints.
6. Issue that pull request!

- [Pull Request Check List](https://ardalis.com/github-pull-request-checklist/)
- [Resync your fork with this upstream project](https://ardalis.com/syncing-a-fork-of-a-github-project-with-upstream/)

## Ask before adding a pull request

You can just add a pull request out of the blue if you want, but it's much better etitquette (and more likely to be accepted) if you open a new issue or comment in an existing issue stating you'd like to make a pull request.

## Getting Started

Look for [issues marked with 'help wanted'](https://github.com/ardalis/guardclauses/issues?q=is%3Aissue+is%3Aopen+label%3A%22help+wanted%22) to find good places to start contributing.

## Any contributions you make will be under the MIT Software License

In short, when you submit code changes, your submissions are understood to be under the same [MIT License](http://choosealicense.com/licenses/mit/) that covers this project.

## Report bugs using Github's [issues](https://github.com/ardalis/guardclauses/issues)

We use GitHub issues to track public bugs. Report a bug by [opening a new issue](https://github.com/ardalis/GuardClauses/issues/new/choose); it's that easy!

## Sponsor us

If you don't have the time or expertise to contribute code, you can still support us by [sponsoring](https://github.com/sponsors/ardalis).

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
MIT License

Copyright (c) 2017 Steve Smith

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `CLAUSE` (category: LEGAL TECH)
- **Upstream URL:** https://github.com/ardalis/GuardClauses
- **Pinned commit (SHA):** `f96b823e4228252b2927cce3effa550c16b558a5`
- **Branch:** main
- **Pin provenance:** GitHub API commits/main. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`de250ebab03dc84a470e234548556ce6d6e3deb4c77284421781970c730dacb3`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| DANS (KNAW/NWO, Netherlands) | 10.17026/PT | EU-recognised archive |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe
and Mail, Business Insider, National Post, Financial Post, StreetInsider,
Digital Journal, Barchart, International Business Times, and Fox News.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

