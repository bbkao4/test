# test


# 자바 프로젝트 기능 설명서

EAP 지원 시스템의 주요 기능들을 순서대로 설명해 드리겠습니다. 각 기능별로 실행 흐름과 관련 파일들을 정리했습니다.

## 1. 로그인 기능
```
사용자 로그인 → LoginController(@Controller) → LoginService(@Service) → LoginMapper.xml 
→ UserSecurityDetailService(사용자 인증) → UserAuthority(권한 부여)
```
- **관련 파일**: `com.eap.eapsupport.login` 패키지 내의 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@Autowired`, `@RequestMapping`

## 2. 메인 대시보드
```
메인 페이지 접속 → MainController(@Controller) → MainService(@Service) → MainMapper.xml
→ MainContentChartDTO(데이터 전달)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 MainContent 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@ResponseBody`, `@RequestMapping`

## 3. Inform Note 기능
```
글쓰기 → InformNoteController(@Controller) → InformNoteService(@Service) 
→ InformNoteMapper.xml → InformNoteRequestDTO/ResponseDTO(데이터 전달)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 InformNote 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`, `@RequestBody`

## 4. 공지사항(Notice) 기능
```
공지사항 조회/작성 → NoticeController(@Controller) → NoticeService(@Service) 
→ NoticeMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 Notice 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@GetMapping`, `@PostMapping`

## 5. 일일 보고서(Daily Report) 기능
```
보고서 생성/조회 → DailyReportController(@Controller) → DailyReportService(@Service) 
→ DailyReportMapper.xml → DailyEmployeeInfoDTO(데이터 전달)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 DailyReport 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 6. ITSM 이슈 관리 기능
```
이슈 등록/조회 → ITSMIssueManagementController(@Controller) → ITSMIssueManagementService(@Service) 
→ ITSMIssueManagementMapper.xml → ITSMIssueDTO(데이터 전달)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 ITSMIssueManagement 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`, `@RequestParam`

## 7. ITSM 작업 관리 기능
```
작업 등록/조회 → ITSMWorkManagementController(@Controller) → ITSMWorkManagementService(@Service) 
→ ITSMWorkManagementMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 ITSMWorkManagement 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 8. ITS 작업 정보 기능
```
작업 정보 조회 → ITSWorkInfoController(@Controller) → ITSWorkInfoService(@Service) 
→ ITSWorkInfoMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 ITSWorkInfo 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@GetMapping`

## 9. ITS 작업 인터페이스 기능
```
인터페이스 호출 → ITSWorkInterfaceController(@Controller) → ITSWorkInfoService(@Service) 
→ [MariaDB/MSSQL/Oracle]ITSInfoMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 ITSWorkInterface 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 10. EAP 유지보수 기능
```
유지보수 정보 관리 → EAPMaintenanceController(@Controller) → EAPMaintenanceService(@Service) 
→ MSSQLEAPMaintenanceMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 EAPMaintenance 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 11. 스마트 EAP 인터페이스 기능
```
스마트 EAP 연동 → SmartEAPInterfaceController(@Controller) → SmartEAPInterfaceService(@Service) 
→ [MariaDB/MSSQL]SmartEAPMapper.xml
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 SmartEAPInterface 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 12. 트렌드 분석 기능
```
데이터 분석 → TrendAnalysisController(@Controller) → TrendAnalysisService(@Service) 
→ TrendAnalysisMapper.xml → ResourceChartRequestDTO/ResponseDTO(데이터 전달)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 TrendAnalysis 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@RequestMapping`

## 13. 이메일 발송 기능
```
이메일 전송 요청 → EmailController(@Controller) → EmailService(@Service) 
→ EmailRequestDTO(데이터 전달) → MailConfig(이메일 설정)
```
- **관련 파일**: `com.eap.eapsupport.controller_service` 내 Email 관련 클래스들
- **주요 어노테이션**: `@Controller`, `@Service`, `@PostMapping`

## 14. 스케줄러 기능
```
정기 작업 → Scheduler(@Component) → 해당 Service 호출 → 데이터베이스 처리
```
- **관련 파일**: `com.eap.eapsupport.scheduler` 패키지 내 클래스들
- **주요 어노테이션**: `@Component`, `@Scheduled`

## 15. 다중 데이터베이스 연결 기능
```
DB 요청 → DynamicDataSource(라우팅) → [MariaDBConfig/MSSQLConfig/OracleConfig](@Configuration) 
→ 각 데이터베이스 연결
```
- **관련 파일**: `com.eap.eapsupport.configuration` 내 데이터베이스 설정 클래스들
- **주요 어노테이션**: `@Configuration`, `@Bean`, `@Primary`, `@Qualifier`

각 기능은 MVC 패턴(Model-View-Controller)을 따르며, 컨트롤러가 요청을 받아 서비스 계층으로 전달하고, 서비스는 DAO(Data Access Object)를 통해 데이터베이스와 통신합니다. 데이터는 DTO(Data Transfer Object)를 통해 전달됩니다.
