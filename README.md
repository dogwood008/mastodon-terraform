# mastodon-terraform

Boilerplate for running [Mastodon](https://github.com/tootsuite/mastodon) on AWS using [Terraform](https://github.com/hashicorp/terraform) via [CircleCI](http://circleci.com/).

## Usage

1. Fork this repository
1. Enable CircleCI integration
1. Set environment variables on CircleCI
1. Build CircleCI to create resources on AWS
1. Build and push mastodon docker image via [mastodon-docker](https://github.com/r7kamura/mastodon-docker)
1. Run `rails db:setup` by running custom ECS task on AWS console

## Environment variables

### Required

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `TF_VAR_aws_region`
- `TF_VAR_mastodon_db_pass`
- `TF_VAR_mastodon_docker_image_tag`
- `TF_VAR_mastodon_otp_secret`
- `TF_VAR_mastodon_secret_key_base`

### Optional

- `TF_VAR_mastodon_aws_access_key_id`
- `TF_VAR_mastodon_aws_secret_access_key`
- `TF_VAR_mastodon_db_name`
- `TF_VAR_mastodon_db_user`
- `TF_VAR_mastodon_default_locale`
- `TF_VAR_mastodon_email_domain_blacklist`
- `TF_VAR_mastodon_email_domain_whitelist`
- `TF_VAR_mastodon_local_domain`
- `TF_VAR_mastodon_local_https`
- `TF_VAR_mastodon_node_env`
- `TF_VAR_mastodon_node_streaming_api_base_url`
- `TF_VAR_mastodon_node_streaming_cluster_num`
- `TF_VAR_mastodon_node_streaming_log_level`
- `TF_VAR_mastodon_node_streaming_port`
- `TF_VAR_mastodon_paperclip_root_path`
- `TF_VAR_mastodon_paperclip_root_url`
- `TF_VAR_mastodon_paperclip_secret`
- `TF_VAR_mastodon_prepared_statements`
- `TF_VAR_mastodon_s3_bucket`
- `TF_VAR_mastodon_s3_cloudfront_host`
- `TF_VAR_mastodon_s3_enabled`
- `TF_VAR_mastodon_s3_endpoint`
- `TF_VAR_mastodon_s3_hostname`
- `TF_VAR_mastodon_s3_protocol`
- `TF_VAR_mastodon_s3_region`
- `TF_VAR_mastodon_single_user_mode`
- `TF_VAR_mastodon_smtp_auth_method`
- `TF_VAR_mastodon_smtp_delivery_method`
- `TF_VAR_mastodon_smtp_domain`
- `TF_VAR_mastodon_smtp_enable_starttls_auto`
- `TF_VAR_mastodon_smtp_from_address`
- `TF_VAR_mastodon_smtp_login`
- `TF_VAR_mastodon_smtp_openssl_verify_mode`
- `TF_VAR_mastodon_smtp_password`
- `TF_VAR_mastodon_smtp_port`
- `TF_VAR_mastodon_smtp_server`

## Resources

This boilerplate will create the following resources:

- module.mastodon.aws_alb_listener.mastodon
- module.mastodon.aws_alb_target_group.mastodon
- module.mastodon.aws_alb.mastodon
- module.mastodon.aws_autoscaling_group.mastodon
- module.mastodon.aws_cloudwatch_log_group.mastodon
- module.mastodon.aws_db_instance.mastodon
- module.mastodon.aws_db_parameter_group.mastodon
- module.mastodon.aws_db_subnet_group.mastodon
- module.mastodon.aws_ecr_repository.mastodon
- module.mastodon.aws_ecs_cluster.mastodon
- module.mastodon.aws_ecs_service.mastodon_rails_puma
- module.mastodon.aws_ecs_service.mastodon_rails_sidekiq
- module.mastodon.aws_ecs_task_definition.mastodon_node_streaming
- module.mastodon.aws_ecs_task_definition.mastodon_rails_db_migration
- module.mastodon.aws_ecs_task_definition.mastodon_rails_db_set_up
- module.mastodon.aws_ecs_task_definition.mastodon_rails_puma
- module.mastodon.aws_ecs_task_definition.mastodon_rails_sidekiq
- module.mastodon.aws_elasticache_cluster.mastodon
- module.mastodon.aws_elasticache_subnet_group.mastodon
- module.mastodon.aws_iam_instance_profile.mastodon
- module.mastodon.aws_iam_policy_attachment.mastodon_ecs_ec2_instance
- module.mastodon.aws_iam_policy_attachment.mastodon_ecs_service
- module.mastodon.aws_iam_role.mastodon_ec2
- module.mastodon.aws_iam_role.mastodon_ecs
- module.mastodon.aws_internet_gateway.mastodon
- module.mastodon.aws_launch_configuration.mastodon
- module.mastodon.aws_route_table_association.mastodon_a
- module.mastodon.aws_route_table_association.mastodon_c
- module.mastodon.aws_route_table.mastodon
- module.mastodon.aws_security_group.mastodon_alb
- module.mastodon.aws_security_group.mastodon_db
- module.mastodon.aws_security_group.mastodon_elasticache
- module.mastodon.aws_security_group.mastodon_web
- module.mastodon.aws_subnet.mastodon_private_a
- module.mastodon.aws_subnet.mastodon_private_c
- module.mastodon.aws_subnet.mastodon_public_a
- module.mastodon.aws_subnet.mastodon_public_c
- module.mastodon.aws_vpc.mastodon
