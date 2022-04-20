TEST_RESULTS := test_results
RXBOT_OUTPUT := -d $(TEST_RESULTS)
RXBOT_ARGS := -P $(CURDIR) $(RXBOT_OUTPUT)
REBOT := rebot $(RXBOT_ARGS)

ifeq ($(leaf_spine_onboarding),true)
ifeq ($(OR_PODS), testbed1)
SKIP_TAGS_VARS += TOPOLOGY_URL
else ifeq ($(OR_PODS), testbed2)
SKIP_TAGS_VARS += small
else ifeq ($(OR_PODS), testbed3)
SKIP_TAGS_VARS += medium
else ifeq ($(OR_PODS), testbed4)
SKIP_TAGS_VARS += xlarge
endif
endif

.PHONY: test-leaf-spine-onboarding
test-leaf-spine-onboarding:
	@echo HI

