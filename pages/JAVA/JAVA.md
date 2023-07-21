---
title: JAVA (자바)
keywords: java
sidebar: java_sidebar
permalink: java.html
folder: java
---

```java
package com.ezen.spring.form;

import java.util.*;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.bind.annotation.RestController;

@Controller
@RequestMapping("/form")
public class FormController 
{
	@Autowired
	private FormSvc formsvc; 
	@GetMapping("/")
	
	@ResponseBody
	public String index()
	{
		return "Hello";
	}
	
	@GetMapping("/login")
	public String loginForm()
	{
		return "login/loginForm";
	}
	
	@PostMapping("/login")
	@ResponseBody
	public Map<String, Boolean> loginProc(User user)
	{
		boolean success = formsvc.login(user);
		Map<String, Boolean> map = new HashMap<>();
		map.put("login", success);
		return map;
	}
	
	// id, pwd를 파라미터로 받아서 users.txt 파일에 한 행으로 저장하고
	// 그 결과를 성공/실패 메시지로 화면에 표시한다. 
	@GetMapping("/save")
	@ResponseBody
	public Map<String, Boolean> save(User user)
	{
		return null;
	}
	
}

```