# Microsoft Graph Web API Template

[English](https://github.com/chenxizhang/dotnetcore-office365dev-templates/blob/master/dotnetcore-graph-webapi/README.md) | [简体中文](https://github.com/chenxizhang/dotnetcore-office365dev-templates/blob/master/dotnetcore-graph-webapi/lang/zh-cn/README.md) | [繁體中文](https://github.com/chenxizhang/dotnetcore-office365dev-templates/blob/master/dotnetcore-graph-webapi/lang/zh-tw/README.md)

> Author：Ares Chen @ 2018/5/1

## Overview

This project template can help you quickly create a web api project, and can accept client calls, through the On-Behalf-Of grant flow to achieve the function of calling a Microsoft Graph as a user, to achieve the following function

1. Read the basic information of the current user

The template supports both ``global`` and `gallatin` versions.

## Preparation

In order to use this template, you'd better be able to register an application yourself. If you are not familiar with this concept, please refer to the description of [Microsoft Graph overview] (https://github.com/chenxizhang/office365dev/blob/master/docs/microsoftgraphoverview.md).

Regardless of whether you are using an international or a domestic version, you can only use the AAD 1.0 registration method at <https://portal.azure.cn>. Please refer to [this article] (https://github.com/chenxizhang/office365dev/blob/master/docs/applicationregisteration.md).

This template example requires at least one delegated permission

1. User.Read

This template implements a complete On-Behalf-Of grant flow. That is, the client application obtains the access permission from Azure AD first, and then when the middle-tier service is invoked, the service layer uses the client's Access_Token to exchange itself. The Access_Token looks as if the client is accessing it. About this scenario, and how to configure On-Behalf-Of applications and permissions, please refer to the <https://github.com/chenxizhang/active-directory-dotnet-webapi-onbehalfof> description here. You need to register two applications.

## Installation

You can install this project template with `dotnet new -i chenxizhang.dotnetcore.msgraph.webapi.CSharp`.

## Use

There are several scenarios for this template, as follows

1. The simplest usage `dotnet new graphwebapi` will create a template implementation that you will use to access Office 365 International using a clientid I ​​created in advance.
1. By explicitly specifying the `clientid` and `secret` parameters, the `tenantid` parameter, and the `obo-console-clientid` parameter, explicitly use your application to access Office 365. This is what I recommend most, the syntax is dotnet New graphwebapi --clientid The application number you created --secret your key --tenantid your tenant number --obo-console-clientid the application number you registered for the client. On how to get `tenantid`, you can also get it through the PowerShell method described in [my article] (http://www.cnblogs.com/chenxizhang/p/7904293.html).
1. With the `instance` parameter, specify whether you want to access the international or domestic version. The international version is the default, and if you want to specify the domestic version, you need to use the following syntax: `dotnet new graphwebapi --instance gallatin --clientid your-applicationid --secret your-key`.
1. Specify the version of the Graph API you want to access via the `version` parameter. The default is `v1.0`. Currently `beta` is also supported.

There are also two common parameters

1. By specifying `name` you can change the name of the project generated by the template, as well as the default namespace name. For example, `dotnet new graphwebapi -n mynamespace`.
1. You can specify to generate a new project directory by specifying ʻoutput`. For example, `dotnet new graphwebapi -o test`.

Once the project is created, you can run it directly from `dotnet run` or edit it in `Visual Studio Code` and run it again.

1. Read the basic information of the current user

## Uninstall

You can uninstall the current project template with `dotnet new -u chenxizhang.dotnetcore.msgraph.webapi.CSharp`.