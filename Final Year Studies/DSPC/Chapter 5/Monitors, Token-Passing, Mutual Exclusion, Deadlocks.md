
## Token Passing

## Suzuki Kasami Algorithm

> An algorithm for mutual exclusion

```

procedure SuzukiKasami(pid)
  sequenceNumber := 0
  token := false

  while true do
    if (not token) and (wantToEnterCriticalSection) then
      sendRequestMessage(pid, sequenceNumber)
      waitUntilTokenIsGranted()
      enterCriticalSection()

    if (inCriticalSection) then
      executeCriticalSectionCode()
      leaveCriticalSection()
      sendReleaseMessage()

    if (not wantToEnterCriticalSection) then
      break

end procedure

procedure sendRequestMessage(pid, sequenceNumber)
  for all processes p do
    send(p, <request, pid, sequenceNumber>)

end procedure

procedure waitUntilTokenIsGranted()
  while (not token) do
    receive(any process, <request, pid, sequenceNumber>)
    if (sequenceNumber >= sequenceNumber) then
      token := true

end procedure

procedure enterCriticalSection()
  criticalSectionCode := true

end procedure

procedure leaveCriticalSection()
  criticalSectionCode := false
  token := false

end procedure

procedure sendReleaseMessage()
  for all processes p do
    send(p, <release, pid>)

end procedure
```

TODO : https://www.youtube.com/results?search_query=suzuki+kasami+algorithm
## Raymond's Tree Algorithm

```
procedure RaymondTree(pid)
  token := false
  parent := get_parent()

  while true do
    if (not token) and (wantToEnterCriticalSection) then
      sendRequestMessage(parent)
      waitUntilTokenIsGranted()
      enterCriticalSection()

    if (inCriticalSection) then
      executeCriticalSectionCode()
      leaveCriticalSection()
      sendReleaseMessage(parent)

    if (not wantToEnterCriticalSection) then
      break

end procedure

procedure sendRequestMessage(parent)
  send(parent, <request, pid>)

end procedure

procedure waitUntilTokenIsGranted()
  while (not token) do
    receive(parent, <token, pid>)
    token := true

end procedure

procedure enterCriticalSection()
  criticalSectionCode := true

end procedure

procedure leaveCriticalSection()
  criticalSectionCode := false
  token := false

end procedure

procedure sendReleaseMessage(parent)
  send(parent, <release, pid>)

end procedure
```


# Deadlocks

> A set of blocked processes each holding a resource and waiting to acquire a resource held by another process in the set.

		