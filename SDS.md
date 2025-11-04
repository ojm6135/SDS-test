## 3. Class diagram



# ProjectService

프로젝트와 관련된 비즈니스 로직의 인터페이스로, 프로젝트 생성, 조회, 수정, 삭제 등의 기능을 정의한다.

## Attributes

| Name | Type | Visibility | Description |
|------|------|-------------|--------------|
|  |  |  |  |

## Operations

| Name | Return Type | Visibility | Description |
|------|-----------|----------|--------------|
| createProject(Long userId, ProjectCreationRequestDto projectCreationRequestDto) | Long | public | 새 프로젝트 공고를 생성 |
| getProject(Long projectId) | ProjectDetailResponseDto | public | 특정 프로젝트의 상세 정보를 조회 |
| getProjectSummaries(ProjectSearchCondition condition, Pageable pageable) | Page<ProjectSummaryResponseDto> | public | 검색 조건에 따른 프로젝트 목록을 조회 |
| getProjectSummariesByIds(List<Long> projectIds) | List<ProjectSummaryResponseDto> | public | 주어진 ID 목록에 해당하는 프로젝트 요약 정보를 조회 |
| updateProject(Long userId, Long projectId, ProjectUpdateRequestDto updateDto) | void | public | 프로젝트 정보를 수정 |
| deleteProject(Long userId, Long projectId) | void | public | 프로젝트를 논리적으로 삭제 |


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

| Name | Return Type | Visibility | Description |
|------|-----------|----------|--------------|
| createProject(Long userId, ProjectCreationRequestDto requestDto) | Long | public | 프로젝트 생성 및 리더 팀원 자동 등록 |
| getProject(Long projectId) | ProjectDetailResponseDto | public | 프로젝트 상세 정보와 연관 데이터(포지션, 스킬, 학년 등) 조회 |
| getProjectSummaries(ProjectSearchCondition condition, Pageable pageable) | Page<ProjectSummaryResponseDto> | public | 조건에 맞는 프로젝트 요약 정보 페이지 조회 |
| getProjectSummariesByIds(List<Long> projectIds) | List<ProjectSummaryResponseDto> | public | ID 순서에 맞춰 프로젝트 요약 정보를 조회 |
| updateProject(Long userId, Long projectId, ProjectUpdateRequestDto updateDto) | void | public | 권한 검증 후 프로젝트 정보 수정 |
| deleteProject(Long userId, Long projectId) | void | public | 권한 검증 후 프로젝트 논리적 삭제 |
