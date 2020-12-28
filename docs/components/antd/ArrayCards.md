```tsx
import React from 'react'
import { FormTab, FormItem, Input, ArrayCards } from '@formily/antd'
import { FormProvider, createForm } from '@formily/react'
import { createSchemaField } from '@formily/react-schema-field'
import { Button, Space } from 'antd'
import 'antd/dist/antd.css'

const SchemaField = createSchemaField({
  components: {
    FormItem,
    Space,
    FormTab,
    Input,
    ArrayCards,
  },
})

const range = (count: number) =>
  Array.from(new Array(count)).map((_, key) => ({
    aaa: key,
  }))

const form = createForm()

export default () => {
  return (
    <FormProvider form={form}>
      <SchemaField>
        <SchemaField.Array
          name="array"
          title="数组项"
          maxItems={3}
          x-component="ArrayCards"
        >
          <SchemaField.Object>
            <SchemaField.Void x-component="ArrayCards.Index" />
            <SchemaField.String
              name="input"
              x-decorator="FormItem"
              required
              x-component="Input"
            />
            <SchemaField.Void x-component="ArrayCards.Remove" />
            <SchemaField.Void x-component="ArrayCards.MoveUp" />
            <SchemaField.Void x-component="ArrayCards.MoveDown" />
          </SchemaField.Object>
          <SchemaField.Void
            x-component="ArrayCards.Addition"
            title="添加条目"
          />
        </SchemaField.Array>
      </SchemaField>
    </FormProvider>
  )
}
```