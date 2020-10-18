# SpringBatch
스프링배치 샘플 코드

### 특정 Job을 실행시킬 수 있도록 한다.

- 테스트 시나리오

```
두개의 Job(stepNextConditionalJob, simpleJob) 이 작성되어 있으며,
'stepNextConditionalJob' 을 단독 실행한다.

jobParameters로 'version=1' 을 넘겨본다.

jobParameters를 바꾸어 보며 실행해본다.

[예상결과] 
	- stepNextConditionalJob 단독 실행.
	- 동일한 파라미터로 재실행시 실행 오류
```

✅ 동일한 Job이 Job Parameter가 달라지면 그때마다 BATCH_JOB_INSTANCE에 생성되며,

동일한 Job Parameter는 여러개 존재할 수 없다.

- applicatiom.yml

```
batch:
    job:
      names: ${job.name:NONE} # 특정 Job 실행,
```

- program arguments

```
--job.name=stepNextConditionalJob version=1
```