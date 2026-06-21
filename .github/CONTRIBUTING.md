# Guidelines for Getting Help with UserFrosting

**Before** you open a new issue or ask a question in chat, you **must** read these guidelines. If it is evident from your issue that you failed to research your question properly, your issue may be closed without being answered.

## Troubleshooting

There are a few common stumbling blocks that new users face when setting up UserFrosting for the first time. If you are new to the current version of UserFrosting, please first look at the [basic requirements and installation instructions](https://learn.userfrosting.com/installation/requirements/basic-stack).

If you don't find what you're looking for in the troubleshooting page, then please check the [existing issues](https://github.com/userfrosting/monorepo/issues), both opened and closed. Your question may have already been asked and answered before!

You can also search for help on Stack Overflow. In addition to the tags for the components that UF builds upon, such as [Slim](http://stackoverflow.com/questions/tagged/slim), [Twig](http://stackoverflow.com/questions/tagged/twig), [Eloquent](http://stackoverflow.com/questions/tagged/eloquent), [Vue 3](https://stackoverflow.com/questions/tagged/vuejs3), there is also a [UserFrosting tag](http://stackoverflow.com/questions/tagged/userfrosting) as well.

There are also tags for the utilities upon which UserFrosting depends, such as [Composer](http://stackoverflow.com/questions/tagged/composer-php) and [Git](http://stackoverflow.com/questions/tagged/git).

## Asking for Help

In general, the [Github issue tracker](https://github.com/userfrosting/monorepo/issues) should only be used for bug reports. If you're just having trouble getting something to work, you should first ask your question in [chat](https://chat.userfrosting.com) or [Github Discussions](https://github.com/orgs/userfrosting/discussions). 

On Github, Chat, and Discussions, please keep in mind the following:

1. Remember that courtesy and proper grammar go a long way. Please take the time to craft a **precise, polite issue**. We will do our best to help, but remember that this is an open-source project - none of us are getting paid a salary to develop this project, or act as your personal support hotline :wink:

2. Report any errors in detail. Vague issues like "it doesn't work when I do this" are not helpful. Show that you have put some effort into identifying the cause of the error.

3. You should also mention the version of UserFrosting that you are using.

4. Post a detailed error message. There are three main places where you may find error messages:

- Non-fatal PHP errors will be logged in your UserFrosting error log. Look for your `app/logs/userfrosting.log` file.

- Frontend (Javascript-related) errors: in your browser's Javascript console. See [this guide](https://learn.userfrosting.com/troubleshooting/debugging) to using your browser console.

You should also try testing your code in a local development environment, to separate **code-related** issues from **server** issues. In general, we recommend that you install a local development server on your computer, rather than [testing your code directly on the production server](https://pbs.twimg.com/media/BxfENwpIYAAcHqQ.png). This means you can test your code directly on your own computer, making development faster and without the risk of exposing sensitive information to the public.

## Contributing to the Codebase

We welcome your technical expertise! But first, please join us in [chat](https://chat.userfrosting.com) to discuss your proposed changes/fixes/enhancements before you get started. One member of our development team will usually be around.

Please also be sure to read our [style guidelines](./STYLE-GUIDE.md).

## Monorepo structure

The UserFrosting codebase is organized as a monorepo, which means that all of our code is stored in a single repository. This includes the main UserFrosting (skeleton), as well as other sprinkles (Admin, Account, Framework, etc.). Each packages is automatically split into a read-only git repository when changes are pushed. 

All changes **must be made in the monorepo**. 

One exception is the Learn documentation and any other related projects. Changes to the Learn documentation should be made in the [`learn`](https://github.com/userfrosting/learn) repository. 

### Branches

Branch represents a specific version. For example, `6.0` represents the 6.0 version, `6.1` represents the 6.1 version, and so on. Branches are always numbered as `major.minor`. The next unreleased patch version (e.g. `6.0.1`) should sit in its minor version branch. 

For example, if we are currently working on `6.0.1`, the code should be in the `6.0` branch. When `6.0.1` is released, the code should be merged into the `6.1` branch, which will then become the new development branch for the next minor version.

Incomplete code must be staged in a draft Pull Request on a `feature-*` or `develop-*` branch. These branches should be deleted after the code is merged into the main development branch (e.g. `6.1`).

### Breaking Changes
Breaking changes should be introduced in a major release, and the version number should be updated accordingly (e.g. from from `6.1` to `6.2`, or `6.x` to `7.0`).

Breaking changes should be documented in the `CHANGELOG.md` file, and a clear migration guide should be provided to help users transition to the new version in the Learn documentation.

Breaking changes are considered to include, while not limited to:
1. **New migrations** that need to be run to update the database schema, or changes to existing database structure.
2. **Changes to the skeleton** that require users to update their own skeleton. Patch version **should not** require users to update their code, only update dependencies. Exceptions can be made for non-critical changes that won't affect existing functionality, such as documentation fixes.
3. **Major changes to the API**, such as renaming or removing public methods, changing method signatures, or changing the behavior of existing methods in a way that could break existing code.
4. **Major changes to the frontend**, such as renaming or removing public components, changing component props, or changing the behavior of existing components in a way that could break existing code. 
5. **Changes to the UI/UX design** of the frontend is considered a breaking change, unless it's to fix an existing issue and doesn't requires the user to update their code (See rule #2).
6. Etc.

### Releases

After every minor or major release, a new version-bumped branch should be created. For example, when releasing `6.2`, a new `6.3` branch must be created for the next minor version. `CHANGELOG.md` should also be updated and the associated tag should be created on Github.

#### Alpha/beta/RC releases

During alpha/beta/RC, a release candidate always sits on the version branch. Release should be numbered with the following syntax : `{major}.{minor}.0-{alpha|beta|rc}.{patch}`. For example : `6.2.0-alpha.1`, `6.2.1-beta.1`, `6.2.0-rc.1`, etc. 

Alpha/beta/RC releases are not mandatory for patch version. Usually, an alpha version means no documentation is ready yet, a beta version means documentation is mostly ready but may still be missing some parts, and an RC version means documentation is ready and the release is almost ready, but we want to give users a chance to test it before the final release.

## Working together

### Issues

Issues are used as a todo list. Each issue represent something that needs to be fixed, added or improved. Be sure to assign issues to yourself when working on something so everyone knows this issue is taken care of.

Issues are tagged to represent the feature or category it refers to. We also have some special labels to help organize issues. These includes:

 - `Good Girst Issue`: If this is your first time contributing to UserFrosting, look for the `good first issue` tag. It's associated with easier issues anyone can tackle.

 - `Help Wanted`: Theses issues have not yet been assigned to anybody. Look for theses when you want to start working on a new issue.

 - `Needs Investigation` : This issue needs to be investigated further before being implemented. It might be a stale issue that's no longer relevant.

 - `New Feature Planning` : Tasks and ideas related to new features that are being planned for the future, but are not yet being worked on.

### Milestones

In order to keep a clear roadmap, milestones are used to assign issues and pull requests to their intended release target. This helps everyone understand issues priority and the expected timeframe for completion.

To maintain a clear history of each milestone, milestones must be closed when completed and the corresponding version released. A new milestone must then be created for the next release. In addition, the milestone version must be updated when new versions are released.

## Learn documentation

The [Learn Documentation](https://learn.userfrosting.com) should always be updated along side code changes.

Changes to the [learn repository](https://github.com/userfrosting/learn) should follow the same logic as the main repository, ie. any changes applied to the `6.0` version/branch should be documented in the learn `6.0` version of the documentation. As of UserFrosting 6, always work on the `main` branch.

Additionally, the `learn` repository can have draft pull request for specific features and fixes not yet released.

## Automatically fixing coding style with PHP-CS-Fixer

[PHP-CS-Fixer](https://github.com/FriendsOfPHP/PHP-CS-Fixer) can be used to automatically fix PHP code styling. UserFrosting provides a project specific configuration file ([`.php_cs`](.php_cs)) with a set of rules reflecting our [style guidelines](./STYLE-GUIDE.md). This tool should be used before submitting any code change to assure the style guidelines are met. Every sprinkles will also be parsed by the fixer.

PHP-CS-Fixer is automatically loaded by Composer and can be used from the UserFrosting root directory :

```
vendor/bin/php-cs-fixer fix
```

Addtionally, [prettier](https://prettier.io) can be used to automatically fix Javascript code styling. UserFrosting provides a project specific configuration file ([`.prettierrc`](.prettierrc)) with a set of rules reflecting our [style guidelines](./STYLE-GUIDE.md). This tool should be used before submitting any code change to assure the style guidelines are met. Every sprinkles will also be parsed by prettier.

Prettier can be used from the UserFrosting root directory :

```
npm run format
```
