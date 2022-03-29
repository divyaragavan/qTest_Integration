TEST_RESULTS := test_results
RXBOT_OUTPUT := -d $(TEST_RESULTS)
RXBOT_ARGS := -P $(CURDIR) $(RXBOT_OUTPUT)
REBOT := rebot $(RXBOT_ARGS)

.PHONY: test-leaf-spine-onboarding
test-leaf-spine-onboarding:
	robot keywords/leaf_spine_onboarding.robot
	$(REBOT) $(TEST_RESULTS)/output.xml
