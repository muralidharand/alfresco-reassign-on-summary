# alfresco-reassign-on-summary
Alfresco Share: make the reassign action visualizable on the summary of the workflow


This is a repository test for the question : https://stackoverflow.com/questions/57219162/capture-alfresco-workflow-task-re-assignment-and-display-it-in-workflow-summary?noredirect=1#comment111426735_57219162

![Img](https://i.stack.imgur.com/Uoil3.png)

### Alfresco Version

Alfresco Community 5.2.g


### ISSUES TO SOLVE

On Alfresco boot while loading the bpmn i get this error:


ERROR [web.context.ContextLoader] [localhost-startStop-1] Context initialization failed
 org.alfresco.error.AlfrescoRuntimeException: 06270001 Workflow deployment failed
        at org.alfresco.repo.workflow.WorkflowDeployer.init(WorkflowDeployer.java:357)
        at org.alfresco.repo.workflow.WorkflowDeployer$1$1.doWork(WorkflowDeployer.java:518)
        at org.alfresco.repo.security.authentication.AuthenticationUtil.runAs(AuthenticationUtil.java:555)
        at org.alfresco.repo.workflow.WorkflowDeployer$1.execute(WorkflowDeployer.java:514)
        at org.alfresco.repo.transaction.RetryingTransactionHelper.doInTransaction(RetryingTransactionHelper.java:464)
        at org.alfresco.repo.workflow.WorkflowDeployer.onBootstrap(WorkflowDeployer.java:509)
        at org.springframework.extensions.surf.util.AbstractLifecycleBean.onApplicationEvent(AbstractLifecycleBean.java:56)
        at org.alfresco.repo.management.SafeApplicationEventMulticaster.multicastEventInternal(SafeApplicationEventMulticaster.java:214)
        at org.alfresco.repo.management.SafeApplicationEventMulticaster.multicastEvent(SafeApplicationEventMulticaster.java:185)
        at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:334)
        at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:954)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:482)
        at org.springframework.web.context.ContextLoader.configureAndRefreshWebApplicationContext(ContextLoader.java:410)
        at org.springframework.web.context.ContextLoader.initWebApplicationContext(ContextLoader.java:306)
        at org.springframework.web.context.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:112)
        at org.alfresco.web.app.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:70)
        at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:5118)
        at org.apache.catalina.core.StandardContext.startInternal(StandardContext.java:5634)
        at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:145)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:899)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:875)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:652)
        at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:679)
        at org.apache.catalina.startup.HostConfig$DeployDescriptor.run(HostConfig.java:1966)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:748)
Caused by: org.alfresco.service.cmr.workflow.WorkflowException: 06270000 Impossibile dispiegare la definizione del workflow.
        at org.alfresco.repo.workflow.activiti.ActivitiWorkflowEngine.deployDefinition(ActivitiWorkflowEngine.java:376)
        at org.alfresco.repo.workflow.WorkflowServiceImpl.deployDefinition(WorkflowServiceImpl.java:237)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:498)
        at org.springframework.aop.support.AopUtils.invokeJoinpointUsingReflection(AopUtils.java:317)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.invokeJoinpoint(ReflectiveMethodInvocation.java:183)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:150)
        at org.alfresco.service.cmr.workflow.WorkflowPermissionInterceptor.invoke(WorkflowPermissionInterceptor.java:64)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
        at org.alfresco.repo.security.permissions.impl.ExceptionTranslatorMethodInterceptor.invoke(ExceptionTranslatorMethodInterceptor.java:53)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
        at org.alfresco.repo.audit.AuditMethodInterceptor.invoke(AuditMethodInterceptor.java:166)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
        at org.springframework.transaction.interceptor.TransactionInterceptor$1.proceedWithInvocation(TransactionInterceptor.java:96)
        at org.springframework.transaction.interceptor.TransactionAspectSupport.invokeWithinTransaction(TransactionAspectSupport.java:260)
        at org.springframework.transaction.interceptor.TransactionInterceptor.invoke(TransactionInterceptor.java:94)
        at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:172)
        at org.springframework.aop.framework.JdkDynamicAopProxy.invoke(JdkDynamicAopProxy.java:204)
        at com.sun.proxy.$Proxy72.deployDefinition(Unknown Source)
        at org.alfresco.repo.workflow.WorkflowDeployer.init(WorkflowDeployer.java:312)
        ... 28 more
Caused by: org.activiti.engine.ActivitiException: Query return 3 results instead of max 1
        at org.activiti.engine.impl.AbstractQuery.executeSingleResult(AbstractQuery.java:187)
        at org.activiti.engine.impl.AbstractQuery.execute(AbstractQuery.java:166)
        at org.activiti.engine.impl.interceptor.CommandInvoker.execute(CommandInvoker.java:24)
        at org.activiti.engine.impl.interceptor.CommandContextInterceptor.execute(CommandContextInterceptor.java:57)
        at org.activiti.spring.SpringTransactionInterceptor$1.doInTransaction(SpringTransactionInterceptor.java:47)
        at org.springframework.transaction.support.TransactionTemplate.execute(TransactionTemplate.java:131)
        at org.activiti.spring.SpringTransactionInterceptor.execute(SpringTransactionInterceptor.java:45)
        at org.activiti.engine.impl.interceptor.LogInterceptor.execute(LogInterceptor.java:31)
        at org.activiti.engine.impl.cfg.CommandExecutorImpl.execute(CommandExecutorImpl.java:40)
        at org.activiti.engine.impl.cfg.CommandExecutorImpl.execute(CommandExecutorImpl.java:35)
        at org.activiti.engine.impl.AbstractQuery.singleResult(AbstractQuery.java:129)
        at org.alfresco.repo.workflow.activiti.ActivitiUtil.getProcessDefinitionForDeployment(ActivitiUtil.java:96)
        at org.alfresco.repo.workflow.activiti.ActivitiTypeConverter.convert(ActivitiTypeConverter.java:150)
        at org.alfresco.repo.workflow.activiti.ActivitiWorkflowEngine.deployDefinition(ActivitiWorkflowEngine.java:367)
        ... 49 more
lug 27, 2020 2:52:50 PM org.apache.catalina.core.StandardContext listenerStart
GRAVE: Exception sending context initialized event to listener instance of class org.alfresco.web.app.ContextLoaderListener
org.alfresco.error.AlfrescoRuntimeException: 06270001 Workflow deployment failed
        at org.alfresco.repo.workflow.WorkflowDeployer.init(WorkflowDeployer.java:357)
        at org.alfresco.repo.workflow.WorkflowDeployer$1$1.doWork(WorkflowDeployer.java:518)
        at org.alfresco.repo.security.authentication.AuthenticationUtil.runAs(AuthenticationUtil.java:555)
        at org.alfresco.repo.workflow.WorkflowDeployer$1.execute(WorkflowDeployer.java:514)
        at org.alfresco.repo.transaction.RetryingTransactionHelper.doInTransaction(RetryingTransactionHelper.java:464)
        at org.alfresco.repo.workflow.WorkflowDeployer.onBootstrap(WorkflowDeployer.java:509)
        at org.springframework.extensions.surf.util.AbstractLifecycleBean.onApplicationEvent(AbstractLifecycleBean.java:56)
        at org.alfresco.repo.management.SafeApplicationEventMulticaster.multicastEventInternal(SafeApplicationEventMulticaster.java:214)
        at org.alfresco.repo.management.SafeApplicationEventMulticaster.multicastEvent(SafeApplicationEventMulticaster.java:185)
        at org.springframework.context.support.AbstractApplicationContext.publishEvent(AbstractApplicationContext.java:334)
        at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:954)
        at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:482)
        at org.springframework.web.context.ContextLoader.configureAndRefreshWebApplicationContext(ContextLoader.java:410)
        at org.springframework.web.context.ContextLoader.initWebApplicationContext(ContextLoader.java:306)
        at org.springframework.web.context.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:112)
        at org.alfresco.web.app.ContextLoaderListener.contextInitialized(ContextLoaderListener.java:70)
        at org.apache.catalina.core.StandardContext.listenerStart(StandardContext.java:5118)
        at org.apache.catalina.core.StandardContext.startInternal(StandardContext.java:5634)
        at org.apache.catalina.util.LifecycleBase.start(LifecycleBase.java:145)
        at org.apache.catalina.core.ContainerBase.addChildInternal(ContainerBase.java:899)
        at org.apache.catalina.core.ContainerBase.addChild(ContainerBase.java:875)
        at org.apache.catalina.core.StandardHost.addChild(StandardHost.java:652)
        at org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:679)
        at org.apache.catalina.startup.HostConfig$DeployDescriptor.run(HostConfig.java:1966)
        at java.util.concurrent.Executors$RunnableAdapter.call(Executors.java:511)
        at java.util.concurrent.FutureTask.run(FutureTask.java:266)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
        at java.lang.Thread.run(Thread.java:748)
Caused by: org.alfresco.service.cmr.workflow.WorkflowException: 06270000 Impossibile dispiegare la definizione del workflow.
        at org.alfresco.repo.workflow.activiti.ActivitiWorkflowEngine.deployDefinition(ActivitiWorkflowEngine.java:376)

