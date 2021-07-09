# config.yml
"# .circleci/config.yml

รุ่น: 2

งาน:

  สร้าง:

    นักเทียบท่า:

      - ภาพ: felicianotech/docker-hugo:0.27.1

    Working_directory: ~/project

    ขั้นตอน:

      - เช็คเอาท์

      - วิ่ง:

          ชื่อ: "สร้างเว็บไซต์เอกสารที่สร้างแบบคงที่ด้วย Hugo"

          คำสั่ง: HUGO_ENV=production hugo -v -s src/

      - ค่าคงที่_to_workspace:

          รูท: /root/project

          เส้นทาง:src/public/

  การทดสอบ html:

    นักเทียบท่า:

      - ภาพ: felicianotech/docker-hugo:0.27.1

    Working_directory: ~/project

    ขั้นตอน:

      - แนบ_workspace:

          ที่: /root/project

      - วิ่ง:

          ชื่อ: "ทดสอบด้วย HTML Proofer"

          command: echo "นี่คือที่ที่เราจะทำการทดสอบด้วย HTML Proofer"

  การทดสอบ ui:

    นักเทียบท่า:

      - ภาพ: felicianotech/docker-hugo:0.27.1

    Working_directory: ~/project

    ขั้นตอน:

      - แนบ_workspace:

          ที่: /root/project

      - วิ่ง:

          ชื่อ: "ทดสอบด้วยซีลีเนียมหรือเบแฮต"

          command: echo "นี่คือที่ที่เราจะเรียกใช้เบราว์เซอร์หัวขาดและทดสอบ UI ของไซต์ของเรา"

  การทดสอบกระบวนการ:

    นักเทียบท่า:

      - ภาพ: felicianotech/docker-hugo:0.27.1

    Working_directory: ~/project

    ขั้นตอน:

      - แนบ_workspace:

          ที่: /root/project

      - วิ่ง:

          ชื่อ: "ทดสอบการคอมมิตสำหรับกระบวนการขององค์กรหรือทีม"

          คำสั่ง: |

            echo "This is where we'd test this commit for things our project wants to enforce"

            echo " such as code formatting, the signing of a CLA, security requirements, etc."

  deploy:

    docker:

      - image: felicianotech/docker-hugo:0.27.1

    working_directory: ~/project

    steps:

      - attach_workspace:

          at: /root/project

      - run:

          name: "Deploy Our Docs Site"

          command: echo "This is where we'd deploy using rsync, awscli, etc."

# Below would be the Workflows specifc config, which we're leaving off for brevity (this example as already lengthy."

 https://circleci.com/blog/circleci-hacks-reuse-yaml-in-your-circleci-config-with-yaml/#:~:text=yml%E0%B8%95%E0%B9%88%E0%B8%AD%E0%B9%84%E0%B8%9B%E0%B8%99%E0%B8%B5%E0%B9%89%3A-,%23,-.circleci/config.yml
