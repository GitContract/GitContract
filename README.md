<p align="center"><img width="240" src="https://github.com/GitContract/GitContract/blob/main/docs/logo.png?raw=true" alt="GitContract logo"></p>


[中文README](https://github.com/GitContract/GitContract/blob/main/docs/README_zh.md)

The purpose of this project is to use Git tools and public repository to store, publicize and trace contracts.

The contract is based on a Github account, so there should be NO personal name or company name.

This repository does not accept any rollback operations and branch operations, and will be public permanently.



### Directory Structure

```
|_ published
|  |_templates
|. |_contracts
|
|_ draft
   |_templates
   |_contracts
```

`published` is used to store formal contract templates and signed contracts. And `draft` is used to store draft contract templates and contracts to be signed. Both `published` and `draft` include `templates` and `contracts` directories, which are used to store contract templates and contracts respectively.



### Release process

The contract template must submit a draft at first. Any contract templates at the draft stage can not be signed. In the draft stage, the submitter of the template should review the rationality of the draft continuously and make adjustments when necessary.

#### Draft stage

1. Fork this repository and clone it
2. Create a directory in `draft->templates`, the name of the directory is the Github username of the employer in the contract subject. Ignore this step if it already exists
3. In the directory created in step 2, put the contract template draft file, which is named as `CONTRACT_TEMPLATE_NAME-VERSION`
4. Submit changes and create a pull request
5. GitContract will review the contract template, mainly to verify whether the submitter's username is the same as the employer's name in the draft, and the sensitive word review

#### Release stage

When the publisher confirms that the current draft template can be officially released, the following process is performed:

1. Create a directory in `published->templates`, the name of the directory is the Github username of the employer in the contract body. Ignore this step if it already exists
2. Move the contract template file that is going to be published under `draft->templates->GITNAME` to the directory created in step 1
3. Submit changes and create a pull request
4. GitContract will review the contract template, mainly to verify whether the submitter's username is the same as the employer's name in the draft, and the sensitive word review



### Contract signing process

The signing of the contract requires the cooperation of both parties. The process is as follows:

1. The hired party forks the repository and clones it
2. Create a directory in `draft->contracts`, the name of the directory is the Github username of the hired party in the contract. Ignore this step if it already exists
3. Put the edited contract file into the directory created in step 2. The file naming method is `CONTRACT_TEMPLATE_EMPLOYER_GITHUB_NAME-CONTRACT_TEMPLATE_NAME-VERSION`
4. Submit changes and create a pull request
5. GitContract will review the draft contract, mainly verifying whether the user name of the submitting party is the same as the name of the hired party in the draft contract, and the sensitive word review
6. The employer forks the repository and clones it
7. Create a directory in `published->contracts`, the name of the directory is the Github username of the hired party in the contract. Ignore this step if it already exists
8. Move the contract file that is going to be published under `draft->contracts->GITNAME` to the directory created in step 7
9. Submit changes and create a pull request
10. GitContract will review the contract, mainly verifying whether the submitter's username is the same as the employer's name in the contract, and the sensitive word review



### File format requirements

#### Contract template

1. NO anti-humane words such as violence, sex trade, politically sensitive, firearms, drugs, hacking etc. shall be included in the contract
2. The contract template is limited to the employer and the employed, and should not include the signing of a third party
3. The variable part of the contract can be marked with `{var}`, where `var` is the name of a custom variable

e.g.

```
I, xxx@email.com, initiated this contract on April 19, 2021.
...
Employee {employee}, the monthly remuneration is ${payment}.
...
```



#### Contract

1. The contract text is a JSON object structure, and each key value should correspond to the variables in the contract template
2. NO anti-humane words such as violence, sex trade, politically sensitive, firearms, drugs, hacking etc. shall be included in the contract

e.g.

```json
{
  "employee": "someone@email.com",
  "payment": 1
}
```

