# Day 06 Understanding Fleet Server and Elastic Agent

## 1. Introduction

**Scenario**: Managing 100 Windows machines with Elastic Agent.

**Options**: Manually configure each agent, use group policy, or utilize a fleet server for centralized management.

## 2. Elastic Agent

**Function**: Unified monitoring for logs, metrics, and other data.

**Policies**: Update and add integrations to control log forwarding to Elasticsearch or Logstash.

**Installation Methods**: Standalone or Fleet-managed.

## 4. Beats vs Elastic Agent

**Beats**: Six types, may require multiple installations on a single host.

**Elastic Agent**: Single agent for various logs, typically sufficient for most use cases.

**Comparison**: [Link provided for detailed differences](https://www.elastic.co/guide/en/fleet/current/beats-agent-comparison.html#additional-capabilities-beats-and-agent)

## 5. Fleet Server

**Function**: Connects Elastic Agents to a fleet for centralized management.

**Benefits**: Easy policy updates, new integrations, data forwarding, agent updates, and enrollment.

**Without Fleet Server**: Manual updates are required, which can be difficult.