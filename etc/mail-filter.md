# Mail.app 필터링 명령어

> 본인 환경에 맞춰 아래 값을 치환해서 사용:
> - `[ENV1]`, `[ENV2]` → 실제 키워드
> - `Custom Folder` → 실제 메일함 이름
> - `Google` → 실제 계정 이름

## Step 1. 계정 이름 확인
```bash
osascript -e 'tell application "Mail" to get name of every account'
```

## Step 2. 받은 편지함 메일 개수
```bash
osascript -e 'tell application "Mail" to get count of messages of inbox'
```

## Step 3. 폴더 목록 확인
```bash
osascript -e 'tell application "Mail" to get name of every mailbox of account "Google"'
```

## Step 4-1. 두 폴더 메일 개수
```bash
osascript <<'EOF'
tell application "Mail"
  set inboxCount to count of messages of mailbox "INBOX" of account "Google"
  set alertCount to count of messages of mailbox "Custom Folder" of account "Google"
  return "INBOX: " & inboxCount & " / Custom Folder: " & alertCount
end tell
EOF
```

## Step 4-2. Custom Folder 최근 5개
```bash
osascript <<'EOF'
tell application "Mail"
  set output to ""
  set msgs to messages 1 thru 5 of mailbox "Custom Folder" of account "Google"
  repeat with msg in msgs
    set output to output & "[" & (date received of msg) & "]" & linefeed
    set output to output & "  " & (subject of msg) & linefeed
    set output to output & "  from: " & (sender of msg) & linefeed & linefeed
  end repeat
  return output
end tell
EOF
```

## Step 4-3. INBOX 최근 5개
```bash
osascript <<'EOF'
tell application "Mail"
  set output to ""
  set msgs to messages 1 thru 5 of mailbox "INBOX" of account "Google"
  repeat with msg in msgs
    set output to output & "[" & (date received of msg) & "]" & linefeed
    set output to output & "  " & (subject of msg) & linefeed
    set output to output & "  from: " & (sender of msg) & linefeed & linefeed
  end repeat
  return output
end tell
EOF
```

## Step 5-1. 윈도우 + 키워드 매칭 개수 (어제 9시 ~ 오늘 9시)
```bash
osascript <<'EOF'
tell application "Mail"
  set todayNine to (current date)
  set hours of todayNine to 9
  set minutes of todayNine to 0
  set seconds of todayNine to 0
  if (current date) < todayNine then
    set endTime to todayNine - (1 * days)
  else
    set endTime to todayNine
  end if
  set startTime to endTime - (1 * days)
  
  set inboxEnv1 to count of (messages of mailbox "INBOX" of account "Google" whose subject contains "[ENV1]" and date received ≥ startTime and date received < endTime)
  set inboxEnv2 to count of (messages of mailbox "INBOX" of account "Google" whose subject contains "[ENV2]" and date received ≥ startTime and date received < endTime)
  set alertEnv1 to count of (messages of mailbox "Custom Folder" of account "Google" whose subject contains "[ENV1]" and date received ≥ startTime and date received < endTime)
  set alertEnv2 to count of (messages of mailbox "Custom Folder" of account "Google" whose subject contains "[ENV2]" and date received ≥ startTime and date received < endTime)
  
  set output to "윈도우: " & (startTime as string) & " ~ " & (endTime as string) & linefeed
  set output to output & "INBOX [ENV1]: " & inboxEnv1 & linefeed
  set output to output & "INBOX [ENV2]: " & inboxEnv2 & linefeed
  set output to output & "Custom Folder [ENV1]: " & alertEnv1 & linefeed
  set output to output & "Custom Folder [ENV2]: " & alertEnv2
  return output
end tell
EOF
```

## Step 5-2. 윈도우 + 키워드 매칭 메일 상세 출력
```bash
osascript <<'EOF'
tell application "Mail"
  set todayNine to (current date)
  set hours of todayNine to 9
  set minutes of todayNine to 0
  set seconds of todayNine to 0
  if (current date) < todayNine then
    set endTime to todayNine - (1 * days)
  else
    set endTime to todayNine
  end if
  set startTime to endTime - (1 * days)
  
  set output to "윈도우: " & (startTime as string) & " ~ " & (endTime as string) & linefeed & linefeed
  set folders to {"INBOX", "Custom Folder"}
  set keywords to {"[ENV1]", "[ENV2]"}
  
  repeat with folderName in folders
    repeat with kw in keywords
      set msgs to (messages of mailbox folderName of account "Google" whose subject contains kw and date received ≥ startTime and date received < endTime)
      set msgCount to count of msgs
      if msgCount > 0 then
        set output to output & "=== " & folderName & " / " & kw & " (" & msgCount & "건) ===" & linefeed
        repeat with msg in msgs
          set output to output & "  [" & (date received of msg) & "]" & linefeed
          set output to output & "  " & (subject of msg) & linefeed
          set output to output & "  from: " & (sender of msg) & linefeed & linefeed
        end repeat
      end if
    end repeat
  end repeat
  
  return output
end tell
EOF
```
