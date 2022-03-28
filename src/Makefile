TEST_RESULTS := test_results
RXBOT_OUTPUT := -d $(TEST_RESULTS)
RXBOT_ARGS := -P $(CURDIR) $(RXBOT_OUTPUT)

ROBOT_DEBUG := -L DEBUG -b debug.txt
ROBOT_ARGS := $(RXBOT_ARGS) $(ROBOT_DEBUG)
ROBOT_TEST_OPTS := --exitonfailure --critical critical --pythonpath . --listener robot_listener.RobotListener
ROBOT := robot $(ROBOT_ARGS)

RXBOT_SUITE = -N qTest_Integration-$(1)
REBOT := rebot $(RXBOT_ARGS)

.PHONY: test-leaf-spine-onboarding
test-leaf-spine-onboarding:
    $(ROBOT) $(call RXBOT_SUITE,leaf-spine-onboarding) $(ROBOT_TEST_OPTS) --exclude skipped --extension rst test_suite/leaf-spine-onboarding
    $(REBOT) $(TEST_RESULTS)/output.xml
