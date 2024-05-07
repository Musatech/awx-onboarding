# ansible-onboarding
Automação Ansible para o processo de onboarding.

      - name: WMS - Create user - AWS Cognito
        cognito_admin_create_user:
          UserPoolId: "us-east-1_n0saO3hxS"
          username: "{{ phone }}"
          desired_delivery_mediums:
            - SMS
          message_action: "SUPPRESS"
          temporary_password: Musa@123
          user_attributes:
            - Name: "phone_number"
              Value: "{{ phone }}"
            - Name: "email"
              Value: "{{ email }}"
            - Name: "email_verified"
              Value: "true"
            - Name: "phone_number_verified"
              Value: "true"
        environment:
          AWS_ACCESS_KEY_ID: "{{ lookup('env','AWS_ACCESS_KEY_ID') }}"
          AWS_SECRET_ACCESS_KEY: "{{ lookup('env','AWS_SECRET_ACCESS_KEY') }}"
        become: no
