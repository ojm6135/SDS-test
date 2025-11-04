## 3. Class diagram

테스트 - 대형

---

# ProjectService

프로젝트와 관련된 비즈니스 로직의 인터페이스로, 프로젝트 생성, 조회, 수정, 삭제 등의 기능을 정의한다.

## Attributes

| Name | Type | Visibility | Description |
|------|------|-------------|--------------|
| (none) |  |  | 인터페이스이므로 필드 없음 |

## Operations

| Name | Argument | Returns | Description |
|------|-----------|----------|--------------|
| createProject | Long userId, ProjectCreationRequestDto projectCreationRequestDto | Long | 사용자가 새 프로젝트를 생성 |
| getProject | Long projectId | ProjectDetailResponseDto | 특정 프로젝트 상세 조회 |
| getProjectSummaries | ProjectSearchCondition condition, Pageable pageable | Page<ProjectSummaryResponseDto> | 검색 조건과 페이지 정보를 기반으로 프로젝트 요약 리스트 조회 |
| getProjectSummariesByIds | List<Long> projectIds | List<ProjectSummaryResponseDto> | 특정 프로젝트 ID 목록에 해당하는 요약 정보 조회 |
| updateProject | Long userId, Long projectId, ProjectUpdateRequestDto updateDto | void | 프로젝트 정보 수정 |
| deleteProject | Long userId, Long projectId | void | 프로젝트 삭제 |


---

# ProjectServiceImpl

[ProjectService](#projectservice) 인터페이스의 구현체로, 실제 데이터베이스 접근 및 비즈니스 로직을 수행한다.

## Attributes

| Name | Type | Visibility | Description |
|------|------|-------------|--------------|
| projectRepository | ProjectRepository | private | 프로젝트 엔티티 접근을 위한 리포지토리 |
| userRepository | UserRepository | private | 사용자 검증을 위한 리포지토리 |
| projectMapper | ProjectMapper | private | DTO ↔ 엔티티 변환을 담당하는 매퍼 |

## Operations

| Name | Argument | Returns | Description |
|------|-----------|----------|--------------|
| createProject | Long userId, ProjectCreationRequestDto projectCreationRequestDto | Long | `ProjectService`의 createProject 구현체로, 사용자 검증 및 프로젝트 저장 처리 |
| getProject | Long projectId | ProjectDetailResponseDto | 프로젝트 상세 조회 로직 구현 |
| getProjectSummaries | ProjectSearchCondition condition, Pageable pageable | Page<ProjectSummaryResponseDto> | 검색 조건을 기반으로 프로젝트 리스트 조회 구현 |
| getProjectSummariesByIds | List<Long> projectIds | List<ProjectSummaryResponseDto> | 프로젝트 ID 목록 기반의 요약 정보 조회 구현 |
| updateProject | Long userId, Long projectId, ProjectUpdateRequestDto updateDto | void | 프로젝트 수정 로직 구현 (사용자 권한 포함) |
| deleteProject | Long userId, Long projectId | void | 프로젝트 삭제 로직 구현 (Soft delete 또는 물리 삭제) |
