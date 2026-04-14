# 변경 대상 파일 (코드 참조)

ooye-app (`/Users/juneui/Documents/develop/ooye-app/src/`) 기준.

## 파일 목록

| 파일 | 현재 역할 |
|---|---|
| `shared/hooks/use-subscription.ts` | 구독 로직, 다이얼로그 텍스트, 알림 권한 체크 |
| `shared/ui/notify-button/notify-button.tsx` | 좋아요/구독 버튼 컴포넌트 |
| `shared/ui/toast/toast.tsx` | 구독 성공 토스트 |
| `shared/ui/icons/subscription-icons.tsx` | 하트 아이콘 (벨 아이콘 추가 필요) |
| `features/creator/components/creator-detail/creator-footer.tsx` | 크리에이터 상세 하단 버튼 |
| `features/creator/components/creator-detail/creator-profile.tsx` | 크리에이터 프로필 버튼 |
| `features/schedule/components/campaign-detail/campaign-footer.tsx` | 공구 상세 하단 버튼 |
| `features/home/components/home-header/home-header.tsx` | 홈 서브탭 ("좋아요") |
| `features/home/widget/likes-content/likes-content.tsx` | 홈 좋아요 탭 콘텐츠, 추천 카드 |
| `features/home/components/likes-empty-state/likes-empty-state.tsx` | 빈 상태 텍스트, 다이얼로그 |
| `features/search/widget/search-results-content/search-results-content.tsx` | 검색 결과 버튼/아이콘 |
| `features/notification/components/notification-bell-button/notification-bell-button.tsx` | 관심 탭 내 아이콘 버튼, accessibility |
| `app/(tabs)/_layout.tsx` | GNB 탭 라벨 |
| `app/(tabs)/notification.tsx` | 관심 탭 화면, 에러 메시지 |
| `shared/providers/notification-permission-provider.tsx` | 알림 권한 체크 로직 (분리 시 변경) |
| `remotes/subscription/` | API 타입, 쿼리, 뮤테이션 (백엔드 분리 시 변경) |

## 데이터 모델 (현재)

- API: `/v1/subscriptions/subscribe` (POST), `/v1/subscriptions/{id}` (DELETE)
- 타입: `SubscriptionResponse`, `EnrichedSubscriptionResponse`
- 구독 타입: `'campaign' | 'creator' | 'keyword'`
- 쿼리 키: `subscriptionQueries.all = ['subscriptions']`

## 분리 시 추가 필요

- follow/bookmark API 엔드포인트 (저장 전용, 알림 없음)
- subscribe API는 알림 전용으로 변경
- `useFollow` / `useBookmark` 훅 신규
- `useSubscription`은 알림 구독 전용으로 리팩토링
- 벨 아이콘 컴포넌트 (`BellOutlineIcon`, `BellFilledIcon`)
- 바텀시트 컴포넌트 (알림 유도)
